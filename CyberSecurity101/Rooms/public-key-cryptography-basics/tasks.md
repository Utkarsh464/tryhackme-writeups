# Public Key Cryptography Basics — Tasks

## Task 1: RSA Fundamentals
- **Purpose:** Understand how RSA encryption works using prime numbers.
- **Skills:** Key generation concept, mathematical basis understanding.
- **Commands:** None.
- **Theory:** RSA relies on the practical difficulty of factoring the product of two large prime numbers. The public key consists of the modulus (n = p * q) and a public exponent (e). The private key includes the private exponent (d). Encryption: c = m^e mod n. Decryption: m = c^d mod n.

## Task 2: Diffie-Hellman Key Exchange
- **Purpose:** Learn how two parties can establish a shared secret over an insecure channel.
- **Skills:** Protocol comprehension, shared secret derivation.
- **Commands:** None.
- **Theory:** Diffie-Hellman allows two parties to each generate a private random number, compute a public value using a shared base and modulus, exchange public values, and independently compute the same shared secret. This secret can then be used as a symmetric key.

## Task 3: Digital Signatures
- **Purpose:** Understand how digital signatures authenticate the sender and ensure message integrity.
- **Skills:** Signing and verification process understanding.
- **Commands:** None.
- **Theory:** A digital signature is created by hashing a message and encrypting the hash with the sender's private key. Anyone with the sender's public key can verify the signature by decrypting the hash and comparing it with a freshly computed hash of the message.

## Task 4: PKI and Certificate Authorities
- **Purpose:** Understand the infrastructure that validates public key ownership.
- **Skills:** Certificate components, chain of trust, CA hierarchy.
- **Commands:** None.
- **Theory:** A Certificate Authority (CA) issues digital certificates binding a public key to an entity. X.509 certificates contain subject, issuer, validity period, public key, and signature. Certificate chains link end-entity certificates through intermediate CAs to a root CA, establishing a hierarchy of trust.
