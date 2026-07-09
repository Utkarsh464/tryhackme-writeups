# Tasks: Cryptography Concepts

## Task 1: Symmetric Encryption
**Purpose:** Understand encryption where the same key encrypts and decrypts.

**Skills:** AES, DES, key distribution problem.

**Theory:** Symmetric encryption uses one shared key for both encryption and decryption. It is fast and suitable for bulk data. AES is the current standard. The key distribution problem is the main disadvantage — both parties need to securely share the key.

**Commands:** `openssl enc -aes-256-cbc -in file.txt -out file.enc`

---

## Task 2: Asymmetric Encryption
**Purpose:** Understand public-key cryptography.

**Skills:** RSA, ECC, public/private key pairs.

**Theory:** Asymmetric encryption uses a public key to encrypt and a private key to decrypt. It solves the key distribution problem but is slower than symmetric encryption. RSA and ECC are widely used. Often combined with symmetric encryption (hybrid cryptosystem).

**Commands:** `openssl genrsa -out private.pem 2048`

---

## Task 3: Hashing
**Purpose:** Understand one-way cryptographic hash functions.

**Skills:** SHA-256, MD5, collision resistance, HMAC.

**Theory:** Hash functions produce a fixed-size digest from any input. They are one-way — you cannot reverse a hash to find the original input. SHA-256 is secure; MD5 is broken. Hashes are used for password storage (with salting), integrity verification, and HMAC for message authentication.

**Commands:** `echo -n "password123" | sha256sum`

---

## Task 4: Digital Signatures
**Purpose:** Understand how signatures provide authenticity and non-repudiation.

**Skills:** Sign, verify, non-repudiation.

**Theory:** A digital signature is created by hashing a message and encrypting the hash with the sender's private key. Anyone with the sender's public key can verify the signature. This provides authentication, integrity, and non-repudiation.

**Commands:** `openssl dgst -sha256 -sign private.pem -out sig.bin file.txt`

---

## Task 5: PKI
**Purpose:** Understand how certificates enable trusted communication.

**Skills:** Certificate Authority, certificates, chain of trust.

**Theory:** PKI binds public keys to identities using digital certificates issued by Certificate Authorities (CAs). A chain of trust extends from root CAs through intermediate CAs to end-entity certificates. PKI is the foundation of HTTPS, email signing, and code signing.

**Commands:** `openssl s_client -connect example.com:443`

---
