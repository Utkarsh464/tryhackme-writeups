# John the Ripper

## Purpose
Offline password cracking tool supporting many hash types (DES, MD5, SHA, NTLM, bcrypt, Kerberos, etc.).

## Installation
```bash
sudo apt install john          # Debian/Ubuntu/Kali
```

## Basic Usage
```bash
john --wordlist=rockyou.txt hash.txt                # Dict crack
john --rules --wordlist=rockyou.txt hash.txt         # With mangling
john --show hash.txt                                 # Show cracked
echo '$2y$10$...' > hash && john hash               # Single hash
unshadow /etc/passwd /etc/shadow > hash && john hash # Crack shadow
```

## Important Commands
- `--wordlist=FILE` — Dictionary file
- `--format=TYPE` — Hash type (e.g., `raw-sha256`, `nt`)
- `--rules` — Apply word-mangling rules
- `--incremental` — Brute-force mode (slow)
- `--show` — Display cracked passwords
- `--users=USER` — Crack specific user
- `--pot=FILE` — Specify pot file (cracked hash db)
- `zip2john`, `rar2john`, `pdf2john`, `ssh2john` — Extract hashes from files

## Typical Workflow
1. Extract hash: `zip2john target.zip > hash.txt`
2. Identify format: `john hash.txt` (auto-detect)
3. Crack: `john --wordlist=rockyou.txt hash.txt`
4. View results: `john --show hash.txt`
5. For slow hashes, use rules: `john --wordlist=x --rules hash.txt`

## Official Documentation
https://www.openwall.com/john/