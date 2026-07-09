# Concepts: Cryptography Concepts

## 1. Symmetric Encryption
Encryption where the same key is used for both encryption and decryption. Algorithms: AES (secure), DES (broken), 3DES (legacy). Fast and efficient for bulk data but has the key distribution problem.

## 2. Asymmetric Encryption
Encryption using a public/private key pair. The public key encrypts, the private key decrypts. Solves key distribution but is computationally expensive. Used for key exchange and digital signatures.

## 3. AES (Advanced Encryption Standard)
The dominant symmetric encryption algorithm. Supports 128, 192, or 256-bit keys. Used by governments, VPNs, and Wi-Fi (WPA2). Considered secure against all practical attacks.

## 4. RSA (Rivest-Shamir-Adleman)
A widely used asymmetric algorithm based on the difficulty of factoring large prime numbers. Key sizes typically 2048 or 4096 bits. Used for encryption and digital signatures.

## 5. SHA-256 (Secure Hash Algorithm)
A cryptographic hash function producing a 256-bit (32-byte) digest. Part of the SHA-2 family. Used in TLS, Bitcoin, and file integrity verification. Collision-resistant for practical purposes.

## 6. HMAC (Hash-based Message Authentication Code)
A mechanism for message authentication using a cryptographic hash function combined with a secret key. Provides both integrity and authenticity verification.

## 7. Digital Signature
A cryptographic construct that binds a signer's identity to a message. Created by signing a hash with the private key. Verified with the public key. Provides non-repudiation.

## 8. PKI (Public Key Infrastructure)
A system of policies, procedures, and technologies for managing digital certificates. Components include Certificate Authorities, registration authorities, and certificate revocation lists.
