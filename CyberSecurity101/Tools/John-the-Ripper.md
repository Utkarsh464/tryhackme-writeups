# John the Ripper

## Purpose
John the Ripper (John) is a fast password cracking tool designed for offline brute-force and dictionary attacks against password hashes. Developed by Solar Designer, it supports hundreds of hash types including Unix crypt, Windows LM/NT, MD5, SHA, bcrypt, scrypt, and many others. John is used in security assessments to test password strength, recover lost credentials, and demonstrate weak password policies.

## Installation
```bash
# Debian/Ubuntu
sudo apt update && sudo apt install john

# Kali Linux (pre-installed)
# Arch Linux
sudo pacman -S john

# macOS
brew install john

# Build from source (recommended for latest features)
git clone https://github.com/openwall/john -b bleeding-jumbo john
cd john/src && ./configure && make

# Community-enhanced version (John Jumbo)
# Contains additional formats, optimizations, and utilities
```

## Basic Usage
```bash
# Crack with default mode (dictionary + rules)
john hash.txt

# Specify hash format explicitly
john --format=nt hash.txt

# Use a specific wordlist
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt

# Show cracked passwords
john --show hash.txt

# Single crack mode (uses login/GECOS information)
john --single hash.txt

# Incremental (brute-force) mode
john --incremental hash.txt
```

## Important Commands
- `--wordlist=<file>` - specify dictionary file for wordlist mode
- `--format=<name>` - force hash type (e.g., `nt`, `sha512crypt`, `bcrypt`)
- `--rules=<rules>` - apply mangling rules to wordlist words
- `--incremental` - brute-force all possible combinations (very slow)
- `--single` - single crack mode using account information
- `--show` - display cracked passwords from session
- `--session=<name>` - name the current cracking session
- `--restore=<name>` - resume a paused session
- `--status` - show status of a running session
- `--pot=<file>` - specify password pot file location
- `--mask` - use mask attack for specific pattern brute-forcing
- `--fork=<num>` - distribute work across CPU cores
- `--node=<min>-<max>/<total>` - distribute across cluster nodes
- `--loopback` - run rules against previously cracked passwords
- `unshadow` - combine /etc/passwd and /etc/shadow for Unix cracking

## Key Features
- **Wordlist Mode** - Tests passwords from a dictionary file, optionally with rules applied
- **Single Crack Mode** - Uses login names, GECOS fields, and user information to generate candidate passwords
- **Incremental Mode** - Exhaustive brute-force, tries all character combinations up to a specified length
- **Marks Attack** - Pattern-based brute-force using placeholders (`?l`, `?u`, `?d`, `?s`) optimized for known password policies
- **External Mode** - Custom cracking routines written in a C-like language
- **Rules Engine** - Word mangling rules for leet speak, capitalization, appending digits, etc.
- **Multi-core/GPU Support** - OpenMP for CPU threading; OpenCL/CUDA for GPU acceleration

## Typical Workflow
1. Extract password hashes from acquired files (e.g., `/etc/shadow`, Windows SAM, database dumps)
2. Identify the hash type using `hashid` or `hash-identifier`
3. Format the hash file correctly (John expects hashes in specific formats)
4. For Unix systems: `unshadow /etc/passwd /etc/shadow > hashes.txt`
5. Run John with appropriate mode: start with wordlist mode using RockYou
6. If wordlist fails, add rules with `--rules=best64` or `--rules=all`
7. Switch to incremental mode for short passwords (1-6 characters)
8. Check cracked passwords with `john --show hashes.txt`

## Advantages
- Supports 300+ hash and cipher types (John Jumbo)
- Highly optimized cracking engine with multi-threading
- Advanced rules engine for efficient word mangling
- Resume capability with session management
- Cluster/distributed cracking support
- Free and open-source with active development
- Extensive community documentation and hash format examples

## Limitations
- CPU-bound (GPU acceleration requires separate configuration with Hashcat)
- Slow for salted hashes and memory-hard algorithms (bcrypt, scrypt, argon2)
- Incremental mode becomes impractical beyond 8 characters
- No built-in hash extraction (requires external tools like Mimikatz, secretsdump.py)
- Wordlist quality is the single biggest factor in success
- Pot file format can create compatibility issues between versions

## Industry Use
John is used by penetration testers for offline password auditing, by forensics analysts to recover encrypted evidence, by system administrators to audit password policies, and by security researchers testing hash algorithm strength. It complements Hashcat, which offers superior GPU performance for many hash types.

## Official Documentation
- Official Site: https://www.openwall.com/john/
- GitHub: https://github.com/openwall/john
- John Jumbo: https://github.com/openwall/john/blob/bleeding-jumbo/README.md
- Wiki: https://openwall.info/wiki/john
- Documentation: https://www.openwall.com/john/doc/
