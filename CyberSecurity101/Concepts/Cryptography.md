# Cryptography

## Definition
Cryptography is the practice and study of techniques for secure communication in the presence of adversaries. It encompasses encryption (scrambling data into ciphertext), decryption (recovering plaintext from ciphertext), hashing, digital signatures, and key exchange. Modern cryptography relies on mathematical problems that are computationally infeasible to reverse (discrete logarithm, integer factorization, elliptic curve problems).

## Why It Matters
Cryptography is the foundation of all information security. It protects data at rest (encrypted files, databases), in transit (TLS, HTTPS, VPNs), and in use (homomorphic encryption). It enables authentication (digital signatures), integrity verification (HMACs), and non-repudiation. Every security professional must understand cryptographic fundamentals to evaluate system security, implement encryption correctly, and avoid common pitfalls.

## Where It Appears in the Path
Cryptography is a core topic in the Cyber Security 101 path. It is prerequisite for understanding HTTPS/TLS, hashing (password storage), RSA, AES, VPNs, wireless security (WPA2/3), digital forensics (encrypted evidence), and blockchain/bitcoin security.

## Prerequisites
- Basic math (modular arithmetic, prime numbers)
- Binary/hexadecimal number systems

## Key Concepts

### Encryption
Converting plaintext into ciphertext using a key. Two main types:
- **Symmetric**: Same key for encryption and decryption (AES, ChaCha20, DES/3DES). Fast, used for bulk data.
- **Asymmetric**: Public key for encryption, private key for decryption (RSA, ECC, ElGamal). Slower, used for key exchange and digital signatures.

### Decryption
Reverting ciphertext to plaintext. In symmetric crypto, the same key does both. In asymmetric, the private key must be kept secret.

### Keys
- Secret/private keys must remain confidential.
- Public keys are shared openly.
- Key length determines security strength. Modern: AES-128/256, RSA-2048+, ECC-256+.

### Cryptographic Primitive Types
- **Block Ciphers**: Encrypt fixed-size blocks (AES-128 = 16-byte blocks).
- **Stream Ciphers**: Encrypt data one bit/byte at a time (ChaCha20, RC4).
- **Hash Functions**: One-way, deterministic, fixed-length output (SHA-256, SHA-3).
- **Message Authentication Codes (MACs)**: Authenticate messages (HMAC, CMAC).
- **Digital Signatures**: Non-repudiation and origin authentication (RSA signatures, ECDSA, EdDSA).

## Symmetric vs Asymmetric Comparison

| Feature | Symmetric | Asymmetric |
|---------|-----------|------------|
| Keys | Single shared key | Public/private key pair |
| Speed | Very fast | Slow (100-1000x slower) |
| Key Distribution Problem | Yes (how to share key securely) | No (public key can be shared openly) |
| Use Cases | Bulk encryption (files, disk, TLS bulk) | Key exchange, signatures, PKI |
| Examples | AES, ChaCha20, DES/3DES | RSA, ECC, Diffie-Hellman |
| Key Length Equivalence | AES-128 ~= RSA-3072 ~= ECC-256 | |

## Common Ciphers

### Classical Ciphers (Historical)
- **Caesar Cipher**: Shift letters by fixed amount. Trivially broken.
- **Vigenère**: Polyalphabetic substitution using keyword. Broken in 19th century.
- **Enigma**: WWII rotor machine. Broken by Alan Turing and Bletchley Park.

### Modern Ciphers
- **AES**: Advanced Encryption Standard — Rijndael cipher. 128/192/256-bit keys.
- **ChaCha20**: Stream cipher designed by Dan Bernstein. Used in TLS, OpenSSH, WireGuard.
- **RSA**: Public-key cryptosystem based on integer factorization.
- **ECC**: Elliptic Curve Cryptography — same security with smaller keys (256-bit ECC ≈ 3072-bit RSA).
- **Diffie-Hellman**: Key exchange over insecure channel.

## Modes of Operation
Block ciphers need modes to encrypt data larger than the block size:
- **ECB**: Each block independently encrypted. Leaks patterns (penguin problem).
- **CBC**: Each block XORed with previous ciphertext. Needs IV.
- **CTR**: Counter mode — essentially turns block cipher into stream cipher.
- **GCM**: Galois/Counter Mode — authenticated encryption (encryption + integrity).
- **CCM**: Counter with CBC-MAC — also authenticated encryption.

## Common Interview Questions
1. **What is the difference between symmetric and asymmetric encryption?** Symmetric uses one key for both operations (fast). Asymmetric uses key pair (slow, solves key distribution).
2. **What is the difference between encryption and hashing?** Encryption is reversible (with key). Hashing is one-way — you cannot recover the original input from the hash.
3. **What is a man-in-the-middle attack on encryption?** Attacker intercepts communication and impersonates both parties. Defeated by certificate authorities and public key pinning.
4. **What is perfect forward secrecy?** Ephemeral key exchange ensures that if long-term private key is compromised, past sessions remain secure. Achieved with DHE/ECDHE.
5. **What is the difference between a block cipher and a stream cipher?** Block cipher encrypts fixed-size blocks. Stream cipher encrypts data continuously. Stream ciphers are generally faster but require unique nonces.
6. **What is a cipher mode of operation and why is ECB bad?** Modes enable encrypting data larger than the block cipher's block size. ECB is bad because identical plaintext blocks produce identical ciphertext blocks, revealing patterns.

## Common Pitfalls
- **Using ECB mode** (leaks patterns)
- **Hardcoding keys** in source code
- **Rolling your own cryptography** (use battle-tested libraries)
- **Reusing nonces/IVs** (breaks security in CTR, GCM modes)
- **Using outdated algorithms** (DES, RC4, MD5, SHA-1)
- **Insufficient key lengths** (RSA < 2048 bits)

## Further Reading
- _Cryptography Engineering_ by Schneier, Ferguson, Kohno
- _Applied Cryptography_ by Bruce Schneier
- [Crypto 101](https://www.crypto101.io/) (free introductory book)
- [Cryptography I on Coursera (Dan Boneh, Stanford)](https://www.coursera.org/learn/crypto)
- [NIST Cryptographic Standards](https://csrc.nist.gov/projects/cryptographic-standards-and-guidelines)
- [Cryptopals Crypto Challenges](https://cryptopals.com/)
