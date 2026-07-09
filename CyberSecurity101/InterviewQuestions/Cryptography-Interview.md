# Cryptography Interview Questions & Answers

## 1. Explain the difference between symmetric and asymmetric encryption.

**Answer:** Symmetric encryption uses the same key for both encryption and decryption. It's fast and efficient for bulk data encryption. Algorithms: AES (128, 192, 256-bit), ChaCha20, Blowfish, 3DES (deprecated). Key exchange is the main challenge (need a secure channel to share the key). Asymmetric encryption uses a public/private key pair. The public key encrypts, the private key decrypts. It's slower (100-1000x) but solves the key distribution problem. Algorithms: RSA, ECC (Elliptic Curve Cryptography), Diffie-Hellman (key exchange only). In practice, hybrid cryptosystems are used: asymmetric encryption for key exchange, symmetric for bulk data (like TLS).

## 2. What is hashing and how is it different from encryption?

**Answer:** Hashing is a one-way function that produces a fixed-size output (digest) from arbitrary input. Properties: deterministic (same input = same output), preimage resistance (cannot reverse), second preimage resistance (cannot find different input with same hash), collision resistance (cannot find two inputs with same hash). Unlike encryption, hashing is NOT reversible - there's no decryption. Uses: password storage, data integrity verification, digital signatures, file identification (checksums). Common algorithms: SHA-256, SHA-3, BLAKE2, MD5/SHA-1 (broken, not for security use). Password hashing: bcrypt, argon2, scrypt, PBKDF2 (include salt and are deliberately slow).

## 3. Explain Public Key Infrastructure (PKI).

**Answer:** PKI is the framework for managing digital certificates and public-key encryption. Components: 1) Certificate Authority (CA) - trusted entity that issues certificates (DigiCert, Let's Encrypt, Sectigo). 2) Registration Authority (RA) - verifies identity before CA issues cert. 3) Certificate Revocation List (CRL) - list of revoked certificates. 4) Online Certificate Status Protocol (OCSP) - real-time certificate status checking. 5) Certificate store - where trusted root CAs are stored. Certificate chain: Root CA (self-signed, highly protected) -> Intermediate CA -> Leaf certificate (server/client). Chain validation ensures trust. Certificate formats: X.509, PEM, DER, PKCS#12.

## 4. How does TLS/SSL work?

**Answer:** TLS (Transport Layer Security) secures communication over networks. Handshake: 1) Client Hello - sends TLS version, cipher suites supported, random number. 2) Server Hello - selects TLS version/cipher, sends its certificate (with public key), random number. 3) Certificate verification - client validates server cert against trusted CAs, checks hostname, revocation, expiration. 4) Key Exchange - typically ECDHE (Ephemeral Diffie-Hellman) for forward secrecy. Client/Server compute shared pre-master secret. 5) Session keys derived from pre-master secret + random numbers. 6) Finished messages confirm handshake. Now encrypted communication begins. TLS 1.3 is faster (1-RTT handshake, removed insecure options).

## 5. What is forward secrecy and why is it important?

**Answer:** Forward secrecy (perfect forward secrecy - PFS) ensures that if a server's long-term private key is compromised, past session keys cannot be derived. Achieved by using ephemeral key exchange (DHE or ECDHE) where temporary keys are generated per session and then discarded. Without PFS: attacker records all encrypted traffic, then steals server's private key later -> can decrypt all past sessions. With PFS: each session uses unique ephemeral keys, so compromising the long-term key only affects future sessions. TLS 1.3 mandates PFS (all cipher suites use ECDHE). DHE uses Diffie-Hellman with ephemeral keys; ECDHE uses elliptic curves (faster, smaller keys).

## 6. Explain the difference between stream ciphers and block ciphers.

**Answer:** Block ciphers encrypt data in fixed-size blocks (e.g., AES: 128-bit blocks). They require a mode of operation (ECB, CBC, GCM, CTR) to handle data larger than one block. ECB (Electronic Codebook) is insecure (identical plaintext blocks produce identical ciphertext). CBC (Cipher Block Chaining) uses IV, chains blocks, but not parallelizable. GCM (Galois/Counter Mode) combines encryption with authentication (AEAD), parallelizable, most recommended. CTR (Counter) converts block cipher to stream-like, parallelizable. Stream ciphers encrypt data one bit/byte at a time, maintaining state. Examples: ChaCha20 (modern, fast, secure), RC4 (broken, deprecated). Stream ciphers are generally faster in software but require careful implementation to avoid key reuse.

## 7. What is a digital signature and how does it work?

**Answer:** A digital signature provides authenticity, integrity, and non-repudiation. Process: 1) Signer creates a hash of the message. 2) Signer encrypts the hash with their private key (this is the signature). 3) Signature + message sent to recipient. 4) Recipient decrypts signature with signer's public key, gets hash. 5) Recipient computes hash of received message. 6) If hashes match, message is authentic and unmodified. Algorithms: RSA (sign then encrypt), DSA, ECDSA, EdDSA (Ed25519). Uses: software distribution (authenticode), document signing (PDF), email (S/MIME, PGP), blockchain transactions, code signing certificates.

## 8. Explain AES encryption in detail.

**Answer:** AES (Advanced Encryption Standard) is a symmetric block cipher with 128-bit blocks and key sizes of 128, 192, or 256 bits. Structure: Substitution-Permutation Network (not Feistel). AES-128 uses 10 rounds, AES-192 uses 12 rounds, AES-256 uses 14 rounds. Each round: SubBytes (non-linear substitution via S-box), ShiftRows (transposition), MixColumns (mixing), AddRoundKey (XOR with round key). The last round omits MixColumns. Key expansion derives round keys from the original key. Modes: AES-CBC (chained, needs padding), AES-GCM (authenticated encryption, recommended), AES-CTR (parallelizable, stream-like), AES-ECB (insecure). AES is approved by NSA for TOP SECRET data (256-bit keys). Hardware acceleration (AES-NI) makes it very fast on modern CPUs.

## 9. What are the common attacks against cryptographic systems?

**Answer:** 1) Brute force - try all possible keys (mitigated by sufficient key length: 128-bit AES is infeasible). 2) Known-plaintext attack - attacker has plaintext/ciphertext pairs. 3) Chosen-plaintext attack - attacker can encrypt arbitrary plaintext (e.g., if they have the public key). 4) Chosen-ciphertext attack - attacker can decrypt chosen ciphertexts (can break RSA without proper padding). 5) Side-channel attacks - timing, power analysis, electromagnetic, cache timing (Spectre/Meltdown). 6) Man-in-the-middle - intercept and modify key exchange. 7) Replay attacks - re-send captured messages (mitigated by nonces/timestamps). 8) Length extension attacks - on hash functions like SHA-256 (mitigated by HMAC/SHA-3). 9) Birthday attacks - finding collisions in hash functions.

## 10. Explain RSA encryption and its security.

**Answer:** RSA is an asymmetric cryptosystem based on the difficulty of factoring large composite numbers. Key generation: 1) Choose two large primes p and q. 2) Compute n = p * q. 3) Compute φ(n) = (p-1)*(q-1). 4) Choose e (typically 65537) coprime to φ(n). 5) Compute d = e^(-1) mod φ(n). Public key: (n, e). Private key: (n, d). Encryption: c = m^e mod n. Decryption: m = c^d mod n. Security relies on factoring difficulty - RSA 2048-bit is considered secure now, RSA 1024-bit is deprecated. RSA 4096-bit is recommended for long-term security. Vulnerabilities: small exponent attacks, padding oracle attacks (PKCS#1 v1.5), timing attacks. OAEP padding is recommended. RSA is slow - typically used for key exchange or signing, not bulk encryption.

## 11. What is the difference between PKCS#1 and PKCS#7/PKCS#12?

**Answer:** PKCS#1 (RSA Cryptography Standard) defines RSA key formats, encryption schemes (RSAES-OAEP), and signature schemes (RSASSA-PSS). PKCS#7 (Cryptographic Message Syntax) defines a standard for signed/enveloped data - the foundation for S/MIME. It can contain certificates, CRLs, and signed data. Files are often .p7b (just certificates, no private key). PKCS#12 (Personal Information Exchange) is a container format for storing private keys with their X.509 certificates. Files are .p12 or .pfx, protected by password. Used for importing/exporting certificates with private keys. OpenSSL commands: `openssl pkcs12 -in file.p12 -out file.pem -nodes`.

## 12. Explain Elliptic Curve Cryptography (ECC).

**Answer:** ECC uses the algebraic structure of elliptic curves over finite fields. Key advantage: shorter key lengths for equivalent security (256-bit ECC ≈ 3072-bit RSA). Curves: NIST P-256 (secp256r1), P-384, P-521, Curve25519 (X25519 for key exchange, Ed25519 for signatures). ECC operations: point addition, point multiplication (scalar multiplication - the hard problem is discrete logarithm). ECDH (Elliptic Curve Diffie-Hellman) for key exchange. ECDSA for signatures. EdDSA (Edwards-curve Digital Signature Algorithm) is a modern alternative with better performance and constant-time execution. ECC is used in TLS, SSH, Bitcoin (secp256k1), and PGP.

## 13. What are cryptographic salts and nonces?

**Answer:** Salt is a random value added to input before hashing. Purpose: prevent rainbow table attacks, ensure identical passwords produce different hashes. Each user gets a unique salt. Salt should be at least 16 bytes, cryptographically random, stored alongside the hash. Nonce is a number used once - prevents replay attacks. Used in: authentication protocols (challenge-response), encryption (GCM/CTR mode), TLS handshake (client/server random). IV (Initialization Vector) is similar to nonce but must be unpredictable (CBC mode) or unique (GCM mode). Non-repeating is critical - reusing a nonce with the same key in GCM/ChaCha20 destroys security.

## 14. Explain the concept of key stretching and derivation.

**Answer:** Key derivation functions (KDFs) derive cryptographic keys from a secret (password, shared secret). Key stretching makes password-based keys computationally expensive to brute-force. PBKDF2 (Password-Based Key Derivation Function 2): iterates HMAC many times, configurable iterations (e.g., 600,000 for SHA-256). bcrypt: adapts to increasing computational power, includes salt, uses Blowfish cipher. scrypt: memory-hard - requires significant RAM, resists ASIC/GPU attacks. argon2: winner of PHC (Password Hashing Competition), has argon2d (data-dependent), argon2i (data-independent), argon2id (hybrid). HKDF (HMAC-based Extract-and-Expand KDF) is used for TLS key derivation. KDF parameters should be tuned to be slow enough to deter attacks but fast enough for good UX.

## 15. What is a certificate transparency log?

**Answer:** Certificate Transparency (CT) is a system for logging and monitoring SSL/TLS certificate issuance. All publicly trusted CAs must submit certificates to CT logs (since 2018, Chrome requires CT). Logs are append-only, Merkle-tree based structures. Benefits: detect rogue CAs issuing certificates for your domain, prevent man-in-the-middle attacks using fraudulent certs, audit CA behavior. SCTs (Signed Certificate Timestamps) prove a certificate was submitted to a log. Embedded SCTs (standard in certificates), TLS extension, or OCSP stapling. Any certificate without CT evidence is now distrusted by modern browsers. Tools: crt.sh (CT log search), Certificate Transparency monitor services.

## 16. Explain the differences between MD5, SHA-1, SHA-2, and SHA-3.

**Answer:** MD5: 128-bit hash, designed by Rivest (1991). Collision attacks demonstrated since 2004 - completely broken for security. SHA-1: 160-bit hash, similar structure to MD5 but stronger. Theoretical attacks improved over time; SHAttered (2017) produced a collision. Deprecated, removed from TLS. SHA-2: SHA-224/256/384/512 - based on Merkle-Damgård structure. Still secure (256-bit provides 128-bit collision resistance). SHA-3: also known as Keccak - based on sponge construction, completely different from SHA-2. Higher security margins, good performance in hardware. Neither SHA-2 nor SHA-3 is broken. SHA-256 is the standard for most applications (TLS 1.3, Bitcoin, PGP). For password hashing, use bcrypt/argon2, not these fast hashes.

## 17. What is the difference between CA-issued certificates and self-signed certificates?

**Answer:** CA-issued certificates are signed by a trusted Certificate Authority (DigiCert, Let's Encrypt, GlobalSign). They are trusted by browsers and OSes because the CA's root certificate is in the trusted store. They require identity validation (DV, OV, EV). Self-signed certificates are signed by their own private key (they are their own CA). They provide the same encryption as CA-issued certs but generate browser trust warnings because they're not in any trusted store. Use cases: development/testing, internal networks (if trust is established), devices with custom trust stores. For production public-facing services, always use CA-issued certificates (Let's Encrypt provides free DV certs). Self-signed certs can be safely used internally if distributed properly.

## 18. How does SSH key-based authentication work?

**Answer:** SSH uses asymmetric cryptography for authentication. Process: 1) User generates key pair (ssh-keygen -t ed25519). 2) Public key appended to remote server's ~/.ssh/authorized_keys. 3) Server challenges client to prove possession of private key. 4) Server generates random number, encrypts with stored public key. 5) Client decrypts with private key, sends back hash. 6) Server verifies correct decryption. Key types: RSA (2048/4096-bit), ECDSA (256/384/521-bit), Ed25519 (most recommended - fast, secure, small keys). SSH also uses host keys (server identity verification). Known_hosts file stores verified host keys. The SSH protocol also negotiates session encryption (typically ChaCha20-Poly1305 or AES-GCM).
