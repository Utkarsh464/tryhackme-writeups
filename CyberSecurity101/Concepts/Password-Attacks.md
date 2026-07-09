# Password Attacks

## Definition
Password attacks are techniques used to gain unauthorized access to systems, accounts, or encrypted data by attempting to discover or bypass password authentication. These attacks range from brute-force (trying all possible combinations) to dictionary attacks (using wordlists), rainbow tables (precomputed hash lookups), social engineering (phishing), and credential harvesting (pass-the-hash, Kerberoasting). Defenders use the same techniques to test password policy strength.

## Why It Matters
Passwords remain the most common authentication mechanism despite their weaknesses. Weak, reused, or compromised passwords cause the majority of data breaches (Verizon DBIR: ~80% of breaches involve compromised credentials). Understanding password attacks is essential for penetration testers (assessing password policies), defenders (enforcing strong authentication), and for understanding how to protect user credentials through salting, proper hashing, and MFA.

## Where It Appears in the Path
Password attacks are covered in the authentication and exploitation modules. They build on cryptography (hashing), networking (remote authentication protocols), and system administration (Windows/Linux password storage). Tools like Hashcat, John the Ripper, Hydra, and Medusa are used extensively.

## Prerequisites
- Hashing fundamentals (MD5, SHA, bcrypt, salt)
- Authentication mechanisms (NTLM, Kerberos, LDAP)
- Basic scripting (for automation)

## Attack Types

### Brute-Force Attack
Try every possible combination of characters up to a given length. Exponential complexity: for 8-character alphanumeric password (a-z, A-Z, 0-9) = 62^8 = 218 trillion combinations. Infeasible for strong passwords. Effective only for short/weak passwords or constrained character sets (numeric PINs: 10^4 = 10,000 for 4-digit PIN).

### Dictionary Attack
Try words from a wordlist (common passwords, dictionary words, leaked password databases). Much more efficient than brute-force because most users choose common words/patterns.

Popular wordlists:
- **rockyou.txt**: 14 million passwords from the RockYou breach. Default wordlist for most tools.
- **SecLists**: Comprehensive collection of wordlists by Daniel Miessler.
- **CrackStation's Password Cracking Dictionary**: 1.5 billion password list.
- **Custom wordlists**: Generated with CeWL (spider target websites), Crunch (pattern-based), or mentalist (mutations).

### Rainbow Table Attack
A precomputed lookup table mapping hash values to plaintext passwords. Extremely fast (constant-time lookup). Defeated by salting — each salt creates a unique hash, requiring a separate rainbow table per salt. Table size grows rapidly with password length and character set.

### Mask Attack
Targeted brute-force where the attacker knows part of the password pattern (e.g., "Summer2024!" — first letter uppercase, year, special character). Hashcat mask syntax: `?u?l?l?l?d?d?d?d?s` for "Summer2024!".

### Rule-Based Attack
Apply transformation rules to dictionary words — leet speak (password → p@ssw0rd), capitalization, appending digits/symbols, reversing words. Hashcat rules and John the Ripper rules are highly configurable. Example: `:c` = capitalize, `$1 $2 $3` = append numbers.

### Hybrid Attack
Combine dictionary words with brute-force extensions (e.g., "password" + "123", "Summer" + "2024"). Very effective against common patterns.

## Credential Harvesting

### Pass-the-Hash (PtH)
Use extracted NTLM password hashes directly for authentication without knowing the plaintext password. Works because NTLM uses the hash as the shared secret. Tools: Mimikatz, Impacket's psexec, CrackMapExec.

### Pass-the-Ticket
Use stolen Kerberos tickets (TGT, service tickets) to authenticate as the user. Mimikatz can extract tickets from LSASS memory.

### Kerberoasting
Request TGS tickets for service accounts, extract encrypted hashes, crack offline. Targets accounts with SPNs (Service Principal Names) in AD.

### AS-REP Roasting
Target accounts without Kerberos pre-authentication required. Extract AS-REP hashes and crack offline.

### Credential Stuffing
Automated login attempts using credential pairs (username:password) from data breaches. Relies on password reuse across services. Mitigated by MFA and credential monitoring (Have I Been Pwned).

## Password Storage Defenses

### Proper Hashing
Use slow, memory-hard hash functions:
- **Argon2id**: Current best practice (PHC winner).
- **scrypt**: Memory-hard, good alternative.
- **bcrypt**: Widely supported, configurable cost.
- **PBKDF2**: NIST-approved, but less resistant to GPU attacks (not memory-hard).

### Salting
Unique random salt per user, stored alongside the hash. Prevents rainbow tables and hides identical passwords.

### Peppering
A secret salt stored separately from the database (in application config, HSM). Adds a layer of security if the database is dumped but the application server is not compromised.

### Account Lockout
Temporarily lock accounts after N failed attempts (e.g., 5 attempts, 15-minute lockout). Prevents online brute-force but can enable denial-of-service.

### Rate Limiting
Slow down repeated authentication attempts by delaying response or requiring CAPTCHA after threshold.

## Cracking Tools

### Hashcat
The fastest password cracker. GPU-accelerated. Supports 300+ hash modes (MD5, SHA1, SHA256, NTLM, bcrypt, Kerberos TGS, etc.).
```bash
hashcat -m 1000 -a 0 hashes.txt rockyou.txt
hashcat -m 1000 -a 6 rockyou.txt ?d?d?d  # Hybrid: wordlist + 3 digits
```

### John the Ripper (John)
Versatile CPU-based cracker. Good for smaller scales and exotic hash types. Strong rule engine.
```bash
john --wordlist=rockyou.txt --rules hashes.txt
john --show hashes.txt  # Show cracked passwords
```

### Hydra / Medusa
Online password attack tools — test credentials against live services (SSH, RDP, FTP, HTTP forms).
```bash
hydra -l admin -P rockyou.txt ssh://192.168.1.100
hydra -L users.txt -P pass.txt rdp://192.168.1.100
```

## Common Interview Questions
1. **What is the difference between brute-force and dictionary attacks?** Brute-force tries all possible character combinations (complete but slow). Dictionary tries words from a list (fast but misses passwords not in the list).
2. **What is a rainbow table and how is it defeated?** Precomputed hash-to-plaintext lookup table for fast cracking. Defeated by salting — unique salt per password makes rainbow tables impractical.
3. **What is the difference between online and offline password attacks?** Online: testing credentials against live service (slow, logged, locked out). Offline: cracking extracted hashes locally (fast, unlimited attempts).
4. **What is pass-the-hash?** Using an NTLM hash directly for authentication without knowing the plaintext password. Works because NTLM uses the hash as the credential.
5. **What are the best practices for storing passwords?** Use Argon2id, unique salt per password, never MD5/SHA-1/SHA-2 directly, never encrypt (hash is one-way), use keyed hashes (HMAC) as additional protection.
6. **What is Kerberoasting?** Requesting Kerberos TGS tickets for service accounts and cracking the extracted hashes offline. Targets service accounts with SPNs in Active Directory.

## Further Reading
- [Hashcat Documentation](https://hashcat.net/wiki/)
- [John the Ripper Documentation](https://www.openwall.com/john/doc/)
- [SecLists (Wordlists)](https://github.com/danielmiessler/SecLists)
- [OWASP Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)
- TryHackMe: Password Attacks room
