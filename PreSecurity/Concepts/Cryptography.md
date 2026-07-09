# Cryptography

## Definition
Cryptography secures data through three main techniques: **Symmetric encryption** (same key for encrypt/decrypt — AES, ChaCha20), **Asymmetric encryption** (public/private key pair — RSA, ECC, Diffie-Hellman), and **Hashing** (one-way, fixed-size output — SHA-256, MD5). **PKI** (Public Key Infrastructure) manages digital certificates and trust via Certificate Authorities (CAs).

## Why It Matters
Cryptography underpins HTTPS, SSH, VPNs, password storage, and digital signatures. Weak algorithms (DES, MD5) enable attacks; proper key management is critical. Security professionals must understand when and how to apply encryption, verify certificates, and detect cryptographic failures.

## Where It Appears in the Path
- Web Hacking Fundamentals
- Security Operations

## Prerequisites
- Basic math concepts (modular arithmetic)

## Key Points
- Symmetric: fast, key distribution problem
- Asymmetric: slower, solves key distribution, enables digital signatures
- Hashing: deterministic, preimage resistant, collision resistant
- PKI: CA issues certificates; revocation via CRL/OCSP

## Common Interview Questions
1. What is the difference between symmetric and asymmetric encryption?
**Answer:** Symmetric uses one key; asymmetric uses a key pair (public/private).
2. What is a hash collision?
**Answer:** Two different inputs producing the same hash output.
3. How does a digital signature work?
**Answer:** Sender hashes data and encrypts the hash with their private key; receiver decrypts with public key and compares hashes.

## Further Reading
- NIST SP 800-175B
- "Applied Cryptography" (Schneier)
- Coursera Cryptography I (Stanford)