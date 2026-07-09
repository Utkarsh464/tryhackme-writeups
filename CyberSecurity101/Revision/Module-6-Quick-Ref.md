# Module 6: Cryptography - Quick Reference

## Core Concepts
- **Encryption** - Converting plaintext to ciphertext (reversible with key)
- **Decryption** - Converting ciphertext back to plaintext
- **Plaintext** - Original readable data
- **Ciphertext** - Encrypted unreadable data
- **Key** - Secret value used for encryption/decryption
- **Cipher** - Algorithm for performing encryption/decryption
- **Cryptanalysis** - Studying systems to break cryptography

## Symmetric Encryption
- **Same key** for encryption and decryption
- Fast, efficient for bulk data
- **Key exchange problem** - must securely share key
- **Algorithms**:
  - **AES** (Advanced Encryption Standard) - Industry standard (128/192/256-bit keys)
  - **ChaCha20** - Modern stream cipher, fast in software
  - **3DES** - Obsolete (deprecated, vulnerable to Sweet32 attack)
  - **Blowfish** - Old but still used in some contexts
- **Modes of Operation**:
  - **ECB** - Insecure (identical blocks = identical ciphertext, shows patterns)
  - **CBC** - Uses IV, chains blocks (needs padding, not parallelizable)
  - **GCM** - Authenticated encryption (AEAD), parallelizable, recommended
  - **CTR** - Stream-like, parallelizable, counter-based
  - **CCM** - Combined CCM mode (CBC-MAC + CTR)

## Asymmetric (Public-Key) Encryption
- **Key pair**: Public key (shared) + Private key (secret)
- Slower (100-1000x slower than symmetric)
- Used for: Key exchange, digital signatures, encryption of small data
- **Algorithms**:
  - **RSA** - Based on factoring large primes (2048/4096-bit recommended)
  - **ECC** - Elliptic Curve Cryptography (256-bit ≈ 3072-bit RSA)
  - **Diffie-Hellman** - Key exchange only (not encryption)
  - **ElGamal** - Based on discrete logarithm
- **Hybrid systems**: Asymmetric for key exchange, symmetric for bulk data (TLS)

## Hashing
- **One-way function** - Cannot reverse
- **Fixed-length output** regardless of input size
- **Properties**: Deterministic, preimage resistant, collision resistant
- **Uses**: Password storage, integrity verification, digital signatures, file checksums
- **Algorithms**:
  - **SHA-256** / **SHA-3** - Current standards (secure)
  - **SHA-1** / **MD5** - Broken (collisions demonstrated, do not use)
  - **BLAKE2** - Fast, modern alternative to SHA
- **Password Hashing** (slow + salt):
  - **bcrypt** - Adaptive, includes salt (most common)
  - **argon2** - Memory-hard, winner of PHC (recommended)
  - **scrypt** - Memory-hard, used in cryptocurrencies
  - **PBKDF2** - Key stretching with many iterations

## Cryptographic Attacks
- **Brute Force** - Try all possible keys (infeasible with sufficient key length)
- **Known-Plaintext** - Attacker has plaintext/ciphertext pairs
- **Chosen-Plaintext** - Attacker can encrypt arbitrary text
- **Chosen-Ciphertext** - Attacker can decrypt chosen ciphertext
- **Side-Channel** - Timing, power, EM, cache analysis
- **MITM** - Intercept key exchange
- **Replay** - Re-send captured messages
- **Birthday Attack** - Find hash collisions
- **Rainbow Table** - Precomputed hash chains (mitigated by salting)
- **Length Extension** - Attack on MD5/SHA-1/SHA-256 (mitigated by HMAC/SHA-3)

## PKI (Public Key Infrastructure)
- **CA** (Certificate Authority) - Trusted entity issuing certificates (DigiCert, Let's Encrypt)
- **RA** (Registration Authority) - Verifies identity before cert issuance
- **Certificate Chain**: Root CA → Intermediate CA → Leaf Certificate
- **CRL** (Certificate Revocation List) - List of revoked certificates
- **OCSP** (Online Certificate Status Protocol) - Real-time cert validation
- **SCT** (Signed Certificate Timestamp) - Proof cert was submitted to CT log
- **Certificate Transparency** - Public logging of all issued certificates
- **Self-signed**: Not trusted by browsers (dev/test only)

## TLS/SSL
- **TLS Handshake**:
  1. Client Hello (TLS version, cipher suites, random)
  2. Server Hello + Certificate + Key Exchange
  3. Certificate verification (CA chain, hostname, expiration)
  4. Key exchange (ECDHE for forward secrecy)
  5. Session key derivation
  6. Encrypted communication begins
- **TLS 1.3**: Faster (1-RTT), removed insecure options, mandatory PFS
- **TLS 1.2**: Still widely used, supports more cipher suites
- **SSL**: Deprecated (SSLv2/v3 broken, POODLE attack)
- **Cipher Suites**: e.g., TLS_AES_256_GCM_SHA384 (key exchange_cipher_MAC)

## Digital Signatures
- **Purpose**: Authentication, integrity, non-repudiation
- **Process**: Hash message → Encrypt hash with private key → Attach to message
- **Verification**: Decrypt signature with public key → Compare hashes
- **Algorithms**: RSA, DSA, ECDSA, EdDSA (Ed25519)
- **Uses**: Code signing, document signing, email (S/MIME, PGP), blockchain

## Key Terms
- **Nonce** - Number used once (prevents replay attacks)
- **Salt** - Random value added to password before hashing (prevents rainbow tables)
- **IV** - Initialization Vector (nonce for first block in CBC/GCM)
- **Forward Secrecy** - Private key compromise doesn't expose past sessions
- **AEAD** - Authenticated Encryption with Associated Data (GCM, ChaCha20-Poly1305)
- **KDF** - Key Derivation Function (derives keys from passwords/shared secrets)
- **HMAC** - Hash-based Message Authentication Code (keyed hash for integrity+auth)
- **MAC** - Message Authentication Code (verifies integrity and authenticity)
- **Entropy** - Measure of randomness (quality of random numbers matters)
- **Perfect Forward Secrecy** - Ephemeral key exchange per session

## Key Length Comparison
| Security Level | Symmetric | RSA | ECC |
|---------------|-----------|-----|-----|
| 80-bit (weak) | 80 | 1024 | 160 |
| 112-bit | 112 | 2048 | 224 |
| 128-bit | 128 | 3072 | 256 |
| 192-bit | 192 | 7680 | 384 |
| 256-bit | 256 | 15360 | 521 |

## Common Commands (OpenSSL)
- Generate RSA key: `openssl genrsa -out key.pem 2048`
- Generate CSR: `openssl req -new -key key.pem -out cert.csr`
- View certificate: `openssl x509 -in cert.pem -text -noout`
- Connect TLS: `openssl s_client -connect example.com:443`
- Generate hash: `openssl dgst -sha256 file.txt`
- Encrypt file: `openssl enc -aes-256-cbc -in file.txt -out file.enc`
- Convert format: `openssl pkcs12 -in cert.p12 -out cert.pem -nodes`
