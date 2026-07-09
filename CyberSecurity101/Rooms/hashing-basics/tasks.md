# Hashing Basics — Tasks

## Task 1: Hash Function Properties
- **Purpose:** Understand what makes a function a cryptographic hash.
- **Skills:** Property identification (deterministic, fast, preimage resistant, collision resistant).
- **Commands:** None.
- **Theory:** Cryptographic hash functions must be deterministic (same input always produces same output), fast to compute, preimage resistant (cannot reverse a hash), second preimage resistant (cannot find a different input with the same hash), and collision resistant (cannot find any two inputs with the same hash).

## Task 2: Common Hash Algorithms
- **Purpose:** Learn about MD5, SHA-1, SHA-2, and SHA-3.
- **Skills:** Algorithm identification, output length awareness.
- **Commands:** `md5sum file`, `sha1sum file`, `sha256sum file`, `openssl dgst -sha256 file`
- **Theory:** MD5 produces 128-bit hashes (32 hex chars) and is cryptographically broken. SHA-1 produces 160-bit hashes and is also broken (SHAttered attack, 2017). SHA-2 (SHA-256, SHA-512) is currently secure. SHA-3 is the newest NIST standard.

## Task 3: Password Hashing and Salting
- **Purpose:** Understand how passwords are stored securely using hashing and salting.
- **Skills:** Salt recognition, algorithm selection for password storage.
- **Commands:** None.
- **Theory:** Passwords should never be stored in plaintext. Hashing alone is insufficient because of rainbow table attacks. A salt (random per-password value) is added before hashing, ensuring identical passwords produce different hashes. Modern password hashing algorithms (bcrypt, argon2, PBKDF2, scrypt) are intentionally slow to resist brute-force attacks.

## Task 4: Hash Verification and Integrity
- **Purpose:** Use hashes to verify file integrity and authenticity.
- **Skills:** Hash comparison, checksum verification.
- **Commands:** `sha256sum downloaded_file.iso`, `echo "hash filename" | sha256sum --check`
- **Theory:** Software distributions often provide checksum files (SHA256SUMS). After downloading, users compute the hash of their file and compare it against the published hash. Matching hashes confirm the file has not been corrupted or tampered with.
