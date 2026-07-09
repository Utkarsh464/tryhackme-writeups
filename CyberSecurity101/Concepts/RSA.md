# RSA

## Definition
RSA (Rivest–Shamir–Adleman) is one of the first practical public-key cryptosystems and is widely used for secure data transmission. It relies on the practical difficulty of factoring the product of two large prime numbers (the "factoring problem"). In RSA, a user generates a public key (used for encryption and signature verification) and a private key (used for decryption and signing).

## Why It Matters
RSA is the most widely deployed asymmetric encryption algorithm. It powers TLS/SSL (HTTPS), SSH, PGP/GPG encryption, digital signatures for software distribution, and certificate authorities. Understanding RSA is essential for evaluating key strength, identifying weak keys (common factors, small exponents), and comprehending how secure web communication actually works.

## Where It Appears in the Path
RSA is covered in the cryptography module after introducing asymmetric encryption principles. It is prerequisite for understanding TLS/HTTPS certificates, SSH key authentication, digital signatures, PGP/GPG, and certificate authorities.

## Prerequisites
- Cryptography fundamentals (symmetric vs asymmetric)
- Basic modular arithmetic (mod operation, prime numbers)
- Hashing (for signatures)

## How RSA Works

### Key Generation
1. Choose two large distinct prime numbers, p and q.
2. Compute n = p × q (n determines key length, e.g., 2048 bits).
3. Compute φ(n) = (p-1) × (q-1) (Euler's totient).
4. Choose public exponent e where 1 < e < φ(n) and gcd(e, φ(n)) = 1. Common e = 65537 (2^16 + 1).
5. Compute private exponent d = e^(-1) mod φ(n) (modular multiplicative inverse).
6. Public key = (n, e). Private key = (n, d). Discard p, q, φ(n) or store securely.

### Encryption
c = m^e mod n (m is plaintext as integer, c is ciphertext)

### Decryption
m = c^d mod n

## Security Foundation
RSA security relies on the fact that:
- Given n (public), it is computationally infeasible to find p and q for sufficiently large n.
- Without p and q, you cannot compute φ(n) and therefore cannot derive d from e.
- Currently, 2048-bit RSA (n = 2^2048) is considered secure. 1024-bit is broken (factoring projects have factored 1024-bit RSA). 4096-bit is recommended for high security.

## Digital Signatures
RSA can also create digital signatures:
1. **Signing**: s = H(m)^d mod n (sign with private key)
2. **Verification**: H(m) = s^e mod n (verify with public key)

The receiver knows the message is authentic (signed by the private key owner) and unmodified. This provides authentication, integrity, and non-repudiation.

## Practical Considerations

### Padding Schemes
Raw RSA (textbook RSA) is insecure — it's deterministic and malleable. Padding adds randomness and structure:
- **PKCS#1 v1.5**: Older, still widely compatible. Vulnerable to Bleichenbacher's attack (1998) in some implementations.
- **OAEP (Optimal Asymmetric Encryption Padding)**: Modern, provably secure (RSA-OAEP). Recommended for encryption.
- **PSS (Probabilistic Signature Scheme)**: Modern padding for RSA signatures (RSA-PSS). Recommended over PKCS#1 v1.5 signatures.

### Key Sizes
| Key Size (bits) | Security Level (bits) | Status |
|-----------------|----------------------|--------|
| 1024 | 80 | Broken (deprecated) |
| 2048 | 112 | Acceptable (current minimum) |
| 3072 | 128 | Good |
| 4096 | 128+ | Strong |

### Performance
RSA is slow compared to symmetric encryption. Encryption with small exponents (e=65537) is faster than decryption (large d). Typical usage: RSA encrypts a symmetric key (e.g., AES-256 key), which then encrypts the bulk data.

## Known Attacks

### Factoring
Given n, compute p and q. For 1024-bit RSA, state-level actors can factor. For 2048-bit, factoring is infeasible with current technology. Shor's algorithm (quantum computing) would break RSA entirely.

### Side-Channel Attacks
Timing attacks, power analysis, electromagnetic emissions. Mitigated by constant-time implementations.

### Chosen-Ciphertext Attacks
Bleichenbacher's attack on PKCS#1 v1.5. Mitigated by using OAEP.

### Small Exponent Attacks
If e is too small (e=3) and m is short, m^e might not wrap mod n (direct root extraction). Avoid — use e=65537.

### Common Factor Attacks
If two RSA keys share a prime factor (due to bad random number generation), their gcd reveals the shared factor. This is how the "ROCA" vulnerability (CVE-2017-15361) and Debian OpenSSH weak keys were exploited.

### Quantum Threat
Shor's algorithm solves factoring in polynomial time on a quantum computer. Once large-scale quantum computers exist, RSA is broken. NIST is standardizing post-quantum cryptography (CRYSTALS-Kyber, CRYSTALS-Dilithium) to replace RSA.

## Common Interview Questions
1. **How does RSA key generation work?** Pick primes p,q. Compute n=p×q, φ(n), choose e, compute d = e^(-1) mod φ(n).
2. **Why is RSA considered secure?** Factoring large products of primes is computationally infeasible. The security depends on the difficulty of the integer factorization problem.
3. **What is the difference between RSA encryption and RSA signing?** Encryption: m^e mod n (public key encrypts, private key decrypts). Signing: H(m)^d mod n (private key signs, public key verifies).
4. **What key size is considered secure for RSA?** Minimum 2048 bits. 1024 bits is broken. 4096 bits for high security.
5. **What is padding and why is RSA padding necessary?** Padding adds randomness and structure, preventing attacks on textbook RSA (malleability, determinism). OAEP for encryption, PSS for signatures.
6. **Can quantum computers break RSA?** Yes — Shor's algorithm factors integers in polynomial time. RSA will be broken by sufficiently large quantum computers. Post-quantum replacements are being standardized.

## Further Reading
- [RFC 8017 — PKCS#1 v2.2 (RSA Cryptography Standard)](https://tools.ietf.org/html/rfc8017)
- [PKCS#1 OAEP and RSA-PSS](https://www.inf.pucrs.br/~calazans/graduate/Criptografia/RSA%20OAEP%20and%20RSA%20PSS.pdf)
- [The Mathematics of RSA](https://www.cs.utexas.edu/~mitra/honors/soln.html)
- [NIST Post-Quantum Cryptography Standardization](https://csrc.nist.gov/projects/post-quantum-cryptography)
- [Cryptographic Right Answers](https://latacora.singles/2018/04/03/cryptographic-right-answers.html)
