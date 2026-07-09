# Hashing Basics — Concepts

## Cryptographic Hash Function
A deterministic algorithm that maps arbitrary input data to a fixed-size output (digest). One-way: the input cannot be derived from the output.

## Digest
The output of a hash function. Also called a hash value, hash code, or checksum. Fixed length regardless of input size (e.g., SHA-256 always produces 256 bits).

## Preimage Resistance
Given a hash value, it should be computationally infeasible to find any input that produces that hash. Also called one-way property.

## Collision Resistance
It should be computationally infeasible to find two different inputs that produce the same hash output. MD5 and SHA-1 no longer satisfy this property.

## Avalanche Effect
A small change in the input (changing one bit) should produce a completely different hash output, with approximately half of the output bits flipping.

## Salt
A random value concatenated with a password before hashing. Prevents rainbow table attacks and ensures that identical passwords produce different hashes.

## Rainbow Table
A precomputed table of hash values for common passwords. Salting renders rainbow tables ineffective because the salt must be known to compute the table.

## Password Hashing Algorithms
Specialized algorithms designed for password storage (bcrypt, argon2, PBKDF2, scrypt). They are intentionally slow and memory-hard to resist brute-force and GPU-based attacks.
