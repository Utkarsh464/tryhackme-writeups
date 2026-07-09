# Cryptography Basics — Tasks

## Task 1: Classical Ciphers
- **Purpose:** Understand historical ciphers and their weaknesses.
- **Skills:** Cipher identification, encryption/decryption of simple ciphers.
- **Commands:** None.
- **Theory:** Classical ciphers include Caesar (shift cipher), monoalphabetic substitution, and Vigenere (polyalphabetic). These are easily broken with frequency analysis or known-plaintext attacks. They illustrate the basic concept of substitution and transposition.

## Task 2: Symmetric Encryption
- **Purpose:** Learn how symmetric encryption uses a single shared key for both encryption and decryption.
- **Skills:** Algorithm identification, key length awareness.
- **Commands:** None.
- **Theory:** In symmetric encryption, the same key encrypts and decrypts. AES is the modern standard with 128, 192, or 256-bit keys. DES (56-bit key) and 3DES are deprecated due to insufficient key length. Block ciphers encrypt fixed-size blocks; stream ciphers encrypt individual bits.

## Task 3: Asymmetric Encryption
- **Purpose:** Understand how public-private key pairs solve the key distribution problem.
- **Skills:** Key pair concept, algorithm identification.
- **Commands:** None.
- **Theory:** Asymmetric encryption uses a mathematically related key pair. The public key encrypts, the private key decrypts. RSA (based on integer factorization) and ECC (based on elliptic curve mathematics) are common. Asymmetric encryption is slower and typically used to exchange symmetric keys.

## Task 4: Encryption in Practice
- **Purpose:** See how encryption is applied in real-world scenarios.
- **Skills:** Encryption mode understanding, IV/nonce recognition.
- **Commands:** None.
- **Theory:** Modern encryption modes (CBC, GCM, CTR) add initialization vectors (IVs) or nonces to ensure that the same plaintext encrypts to different ciphertexts. GCM also provides authentication (AEAD). TLS uses a combination of asymmetric key exchange followed by symmetric bulk encryption.
