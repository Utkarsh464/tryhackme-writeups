# Cryptography Basics — Concepts

## Encryption
The process of converting plaintext into ciphertext using an algorithm and a key. Prevents unauthorized reading of data. Reversible with the correct key.

## Symmetric Encryption
Uses a single shared key for both encryption and decryption. Fast and efficient for bulk data. Challenge is secure key distribution. Examples: AES, DES, ChaCha20.

## Asymmetric Encryption
Uses a mathematically related pair of keys (public and private). The public key encrypts, the private key decrypts. Solves the key distribution problem but is computationally expensive. Examples: RSA, ECC.

## Cipher
An algorithm for performing encryption or decryption. Block ciphers operate on fixed-size blocks (e.g., AES-128 encrypts 16-byte blocks). Stream ciphers operate on individual bits or bytes.

## Key Length
The size of the cryptographic key in bits. Longer keys provide stronger security. AES-128 is considered secure; AES-256 provides a higher safety margin. RSA requires much longer keys (2048+ bits) due to its mathematical structure.

## Initialization Vector (IV) / Nonce
A random value used with a key to ensure that the same plaintext produces different ciphertext each time. Prevents pattern analysis. Must be unique per encryption session.
