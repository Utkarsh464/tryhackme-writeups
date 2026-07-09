# John the Ripper

**John the Ripper** — a fast password hash cracking tool with support for hundreds of hash types.

## Syntax

```
john [options] <hash-file>
```

## Purpose

Crack password hashes using dictionary attacks, brute-force, or rule-based modifications. Used in security assessments to test password strength and recover plaintext passwords from captured hash dumps.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `--wordlist=<file>` | Specify wordlist for dictionary attack |
| `--rules` | Enable word-mangling rules |
| `--format=<type>` | Force hash format (e.g., `--format=raw-md5`) |
| `--show` | Show cracked passwords |
| `--incremental` | Brute-force mode (exhaustive) |
| `--mask=<mask>` | Mask attack for specific patterns |
| `--fork=<N>` | Run N parallel processes |
| `--session=<name>` | Save/restore session state |
| `--pot=<file>` | Custom pot file for cracked hashes |
| `--status` | Show status of a running session |

## Hash Formats

| Hash Type | John Format | Example |
|-----------|-------------|---------|
| MD5 | `raw-md5` | From web app DB dumps |
| SHA-256 | `raw-sha256` | Linux shadow hashes |
| bcrypt | `bcrypt` | Modern web frameworks |
| NTLM | `nt` | Windows password hashes |
| LM | `lm` | Legacy Windows hashes |
| SHA-512 ($6$) | `sha512crypt` | Modern Linux shadow |
| md5crypt ($1$) | `md5crypt` | Older Linux shadow |

## Examples

```bash
# Crack hashes with a wordlist
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt

# Crack with rules enabled
john --wordlist=password.lst --rules hashes.txt

# Show already cracked passwords
john --show hashes.txt

# Force a specific hash format
john --format=raw-md5 --wordlist=rockyou.txt hashes.txt

# Incremental (brute-force) mode — very slow but thorough
john --incremental hashes.txt

# Single crack mode (uses login names and variations)
john --single hashes.txt

# Unshadow — combine /etc/passwd and /etc/shadow
unshadow /etc/passwd /etc/shadow > unshadowed.txt
john unshadowed.txt
```

## Common Mistakes

- Not identifying the hash type first — John needs the correct format or it will waste time on wrong algorithms. Use `hashid` or `hash-identifier` first.
- Using `--incremental` on large hashlists — this can take years. Always start with wordlist + rules.
- Forgetting to unshadow before cracking Linux password files — John requires the combined format.
- Not using a GPU — John supports GPU acceleration (`--devices`) which is orders of magnitude faster for many hash types.
- Ignoring the mangling rules — plain dictionary attacks miss simple variations like `Password1!`.

## Real-World Usage

- **Post-exploitation:** Crack dumped password hashes from `/etc/shadow` or Windows SAM.
- **CTF challenges:** Break hash-protected files, ZIP archives, or Linux user accounts.
- **Password policy auditing:** Verify users are not using weak passwords.
- **Forensics:** Recover passwords from memory dumps or disk images.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed on Kali |
| Windows | Full | Official builds available (JtR Pro includes GUI) |
| macOS | Full | via Homebrew or source compile |

```bash
# Install on Linux
sudo apt install john
```
