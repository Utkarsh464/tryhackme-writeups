# Public Key Cryptography Basics — Concepts

## RSA
An asymmetric encryption algorithm based on the difficulty of factoring large prime products. Used for encryption, digital signatures, and key exchange. Named after Rivest, Shamir, and Adleman.

## Diffie-Hellman (DH) Key Exchange
A protocol that allows two parties to establish a shared secret over an insecure channel. The shared secret is used to derive a symmetric encryption key. Vulnerable to man-in-the-middle attacks without authentication.

## Digital Signature
A cryptographic mechanism that provides authentication, integrity, and non-repudiation. Created by signing a message hash with the sender's private key. Verified using the sender's public key.

## PKI (Public Key Infrastructure)
The framework of policies, procedures, and technologies for managing digital certificates. Includes CAs, Registration Authorities, certificate repositories, and revocation mechanisms.

## Certificate Authority (CA)
A trusted entity that issues and manages digital certificates. CAs validate the identity of certificate requestors before signing. Root CAs are self-signed and serve as trust anchors.

## X.509 Certificate
A standard format for public key certificates. Contains version, serial number, algorithm ID, issuer, validity period, subject, public key, extensions, and CA signature.

## Chain of Trust
A hierarchical trust model where each certificate is signed by the CA above it. The chain ends at a self-signed root CA certificate, which is trusted by the system.
