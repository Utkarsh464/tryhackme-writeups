# Cryptography Interview Questions

## 1. What is the difference between symmetric and asymmetric encryption?
**Answer:** Symmetric encryption uses a single shared key for both encryption and decryption (e.g., AES, DES, ChaCha20). It is fast and suitable for bulk data encryption but requires secure key distribution. Asymmetric encryption uses a public-private key pair: the public key encrypts, the private key decrypts (e.g., RSA, ECC). It solves key distribution but is computationally slower. Hybrid systems combine both: asymmetric for key exchange, symmetric for bulk data.

## 2. Explain AES and RSA.
**Answer:** AES (Advanced Encryption Standard) is a symmetric block cipher with key sizes of 128, 192, or 256 bits. It is the global standard for encrypting data at rest and in transit, used in TLS, file encryption, and disk encryption. RSA (Rivest-Shamir-Adleman) is an asymmetric algorithm based on the difficulty of factoring large prime numbers. It is used for key exchange, digital signatures, and encryption of small data (typically up to the key size, e.g., 2048 or 4096 bits).

## 3. What are the key properties of cryptographic hash functions?
**Answer:** Cryptographic hash functions must have: (1) Determinism — same input always produces same output. (2) Preimage resistance — given a hash, it's infeasible to find the original input. (3) Second preimage resistance — given an input, it's infeasible to find a different input with the same hash. (4) Collision resistance — infeasible to find any two different inputs with the same hash. (5) Avalanche effect — a small input change dramatically changes the output. (6) Fixed output length regardless of input size.

## 4. How do digital signatures work?
**Answer:** A digital signature provides authenticity, integrity, and non-repudiation. The sender hashes the message and encrypts the hash with their private key (signing). The receiver decrypts the signature with the sender's public key, computes the hash of the original message, and compares. If they match, the message is authentic and unmodified. Digital signatures use asymmetric cryptography and are fundamental to code signing, document signing, and TLS certificates.

## 5. What is Public Key Infrastructure (PKI)?
**Answer:** PKI is a framework of policies, procedures, hardware, and software for managing digital certificates and public-key encryption. It includes Certificate Authorities (CAs — issue certificates), Registration Authorities (RAs — verify identity), certificate revocation lists (CRLs) and OCSP (revocation checking), and certificate stores. PKI enables trust on the internet by binding public keys to verified identities, forming the trust chain for HTTPS, email signing, and code signing.

## 6. Explain the TLS handshake process.
**Answer:** The TLS handshake establishes a secure connection: (1) Client sends ClientHello with supported TLS versions, cipher suites, and a random nonce. (2) Server responds with ServerHello (selected cipher), its certificate, and optionally requests client certificate. (3) Client verifies the certificate against trusted CAs, generates a pre-master secret, encrypts it with the server's public key, and sends it. (4) Both sides derive session keys from the pre-master secret. (5) They exchange Finished messages (encrypted) to confirm the handshake succeeded. Symmetric encryption then protects all subsequent data.

## 7. What is the difference between encryption, encoding, and hashing?
**Answer:** Encryption transforms data using a key so it can be decrypted back to original form; it provides confidentiality. Encoding transforms data into a different format (e.g., Base64, ASCII, UTF-8) for compatibility — it is not secret and easily reversible with no key. Hashing produces a fixed-size, irreversible digest of data; it provides integrity verification but cannot be reversed. Confusing these is a common source of security vulnerabilities.

## 8. How should passwords be stored securely?
**Answer:** Passwords must never be stored in plaintext or using simple hashes (MD5, SHA-1). They should be hashed using adaptive, salted hashing algorithms: bcrypt (Blowfish-based, configurable cost factor), Argon2 (winner of the Password Hashing Competition, memory-hard, resistant to GPU/ASIC attacks), or scrypt (memory-hard). Salting (adding a unique random value per password before hashing) prevents rainbow table attacks. A high work factor (cost) makes brute-force attacks computationally expensive.

## 9. What is key exchange and how does Diffie-Hellman work?
**Answer:** Key exchange allows two parties to securely agree on a shared secret over an insecure channel. Diffie-Hellman (DH) works by: both parties agree on public parameters (prime p, generator g). Each selects a private key (a, b) and computes public values (g^a mod p, g^b mod p). They exchange public values. Each computes the shared secret: (g^b)^a = (g^a)^b = g^(ab) mod p. An eavesdropper cannot compute this secret without the private keys. ECDH uses elliptic curve cryptography for equivalent security with smaller key sizes.
