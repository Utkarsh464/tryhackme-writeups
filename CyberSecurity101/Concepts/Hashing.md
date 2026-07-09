# Hashing

## Definition
Hashing is the process of converting any input data (a message, file, password) into a fixed-size string of bytes, typically represented as a hexadecimal value. Hash functions are deterministic (same input → same output), one-way (infeasible to reverse), and collision-resistant (extremely unlikely for two different inputs to produce the same hash). Common hash functions: MD5, SHA-1, SHA-256, SHA-3, BLAKE2.

## Why It Matters
Hashing is critical for data integrity verification, password storage, digital signatures, and file identification. Unlike encryption, hashing is not reversible — this makes it ideal for storing passwords (even if the database is stolen, attackers can't recover the plain passwords). Hash functions are used in TLS certificate validation, Git version control, blockchain, and malware hash databases (VirusTotal, NSRL).

## Where It Appears in the Path
Hashing is covered in the cryptography module. It is prerequisite for password storage (salting, hashing algorithms), password attacks (hash cracking), digital forensics (file integrity, hash sets), digital signatures (RSA), and blockchain security.

## Prerequisites
- Cryptography fundamentals (one-way functions)
- Understanding of binary/hexadecimal representations

## Properties of Cryptographic Hash Functions
1. **Deterministic**: Same input always produces same hash.
2. **Pre-image Resistance (One-way)**: Given a hash H(x), it is infeasible to find x.
3. **Second Pre-image Resistance**: Given x, it is infeasible to find y ≠ x such that H(x) = H(y).
4. **Collision Resistance**: Infeasible to find any two different inputs x, y with H(x) = H(y).
5. **Avalanche Effect**: Changing one bit of input changes ~50% of output bits.
6. **Fixed Output Size**: Regardless of input length, output is always same length.

## Common Hash Functions

### MD5 (Message Digest 5)
128-bit output. Designed by Ron Rivest in 1991. **Broken** — collision attacks demonstrated since 2004. Should never be used for security purposes. Still used for non-security file checksums (quick integrity check).

### SHA-1 (Secure Hash Algorithm 1)
160-bit output. Designed by NSA in 1995. **Broken** — SHAttered attack (2017) demonstrated collision. Deprecated, replaced by SHA-2/SHA-3.

### SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
Family by NSA (2001). Still secure. SHA-256 (256-bit output) is the industry standard. Used in TLS, SSH, IPsec, Git, blockchain (Bitcoin uses double SHA-256).

### SHA-3 (Keccak)
NIST standard since 2015. Different design from SHA-2 (sponge construction). No known practical attacks. Gradual adoption.

### BLAKE2 / BLAKE3
Fast hashing designed by Aumasson et al. BLAKE2 is faster than SHA-2 with equivalent security. BLAKE3 is even faster with parallelization. Used by many modern tools and protocols.

## Password Hashing
Storing passwords requires special hash functions designed to be slow and memory-hard to resist brute-force attacks:

### bcrypt
Based on Blowfish cipher. Configurable cost factor (work factor). Default is 10 (2^10 rounds). Produces output string with algorithm identifier, cost, salt, and hash.

### scrypt
Designed to be memory-hard — requires significant memory to compute. Resists ASIC/GPU attacks. Used by Litecoin and other cryptocurrencies.

### Argon2
Winner of the Password Hashing Competition (2015). Three variants: Argon2d (resists GPU), Argon2i (resists side-channel), Argon2id (hybrid). NIST recommended.

### PBKDF2 (Password-Based Key Derivation Function 2)
Older standard. Configurable iterations (recommended ≥310,000 for SHA-256). Used in WPA/WPA2, iOS, Android. Less memory-hard — more vulnerable to GPU attacks than bcrypt/scrypt/Argon2.

## Salt
A random value concatenated with a password before hashing. Prevents:
- **Rainbow table attacks**: Precomputed hash lookup tables become useless with unique salts.
- **Same-password detection**: Two users with the same password have different hashes.
Salt must be unique per user, cryptographically random, and stored alongside the hash.

## HMAC (Hash-Based Message Authentication Code)
HMAC uses a hash function combined with a secret key to provide message authentication. HMAC-SHA256 is widely used for API authentication, JWT signing, and TLS. HMAC provides both integrity verification and origin authentication.

## Common Attacks on Hash Functions

### Collision Attack
Find two messages with the same hash. MD5 collisions can be generated in seconds. SHA-1 collisions are possible with sufficient computational power (SHAttered required ~6500 CPU years).

### Length Extension Attack
Given H(M), compute H(M || extra) without knowing M. Affects MD5, SHA-1, SHA-2 (not SHA-3). HMAC is immune.

### Rainbow Table Attack
Precomputed lookup table mapping hashes to plaintexts. Defeated by salting.

### Brute-Force / Dictionary Attack
Try many plaintexts until hash matches. Mitigated by slow hash functions (bcrypt/Argon2).

## Common Interview Questions
1. **What is the difference between hashing and encryption?** Hashing is one-way (cannot reverse). Encryption is two-way (can decrypt with key).
2. **Why is MD5 considered broken?** Collision attacks are practically feasible — two different inputs produce the same MD5 hash.
3. **What is salting and why is it important?** Random data added before hashing passwords. Prevents rainbow table attacks and hides identical passwords.
4. **What is the difference between SHA-256 and bcrypt?** SHA-256 is fast (designed for integrity). Bcrypt is slow (designed for password storage). Never use a fast hash for passwords.
5. **What is HMAC and when would you use it?** Hash-based Message Authentication Code — combines hash function with a secret key. Used for API authentication, JWT, TLS record integrity.
6. **What is a rainbow table attack?** Precomputed table of password-to-hash mappings that allows instant lookup. Defeated by salting — salt makes the table useless.

## Further Reading
- [NIST Secure Hashing](https://csrc.nist.gov/projects/hash-functions)
- [Have I Been Pwned](https://haveibeenpwned.com/) (password hash search)
- [CrackStation](https://crackstation.net/) (rainbow table service)
- [OWASP Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)
- `hashcat` and `john` tools for hash cracking
- _Serious Cryptography_ by Jean-Philippe Aumasson
