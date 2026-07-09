# hydra

**THC-Hydra** — a parallelized network login cracker that supports numerous protocols for brute-force attacks.

## Syntax

```
hydra -l <username> -P <password-list> <target> <service>
hydra -L <user-list> -P <password-list> <target> <service>
```

## Purpose

Perform brute-force attacks against network services to discover valid credentials. Supports over 50 protocols including SSH, FTP, HTTP(S), SMB, MySQL, and more. A standard tool for password auditing and penetration testing.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-l` | Single username |
| `-L` | File containing list of usernames |
| `-p` | Single password |
| `-P` | File containing list of passwords |
| `-t` | Tasks per target (threads) |
| `-s` | Custom port number |
| `-V` | Verbose output (shows each attempt) |
| `-f` | Stop after first valid credential found |
| `-o` | Output file for found credentials |
| `-I` | Ignore saved restorations (start fresh) |
| `-e nsr` | Try null password (`n`), same as login (`s`), reversed login (`r`) |

## Supported Services

| Service | Syntax | Example |
|---------|--------|---------|
| SSH | `ssh` | `hydra -l root -P pass.txt 10.10.10.1 ssh` |
| FTP | `ftp` | `hydra -L users.txt -P pass.txt 10.10.10.1 ftp` |
| HTTP POST | `http-post-form` | `hydra -l admin -P pass.txt 10.10.10.1 http-post-form "/login:user=^USER^&pass=^PASS^:F=incorrect"` |
| SMB | `smb` | `hydra -l admin -P pass.txt 10.10.10.1 smb` |
| MySQL | `mysql` | `hydra -l root -P pass.txt 10.10.10.1 mysql` |
| RDP | `rdp` | `hydra -l admin -P pass.txt 10.10.10.1 rdp` |

## Examples

```bash
# SSH brute-force with single username
hydra -l root -P /usr/share/wordlists/rockyou.txt 10.10.10.1 ssh

# FTP brute-force with username list
hydra -L users.txt -P /usr/share/wordlists/rockyou.txt 10.10.10.1 ftp

# HTTP POST form brute-force
hydra -l admin -P pass.txt 10.10.10.1 http-post-form "/login.php:user=^USER^&pass=^PASS^:F=Invalid"

# SMB brute-force, stop at first find
hydra -l administrator -P pass.txt -f 10.10.10.1 smb

# RDP brute-force with custom port
hydra -l admin -P pass.txt -s 3333 10.10.10.1 rdp
```

## Common Mistakes

- Using only one password list — always use the largest, most relevant wordlist (rockyou.txt for real users, common passwords for services).
- Too many threads (`-t 64`) — can lock accounts due to rate limiting or crash the service.
- Forgetting the protocol-specific syntax for HTTP forms — the colon-delimited format is critical.
- Not accounting for account lockout policies — brute-forcing can lock legitimate users out.
- Running on production systems without authorization — illegal and disruptive.

## Real-World Usage

- **Password auditing:** Test strength of corporate passwords against common wordlists.
- **CTF challenges:** Crack login portals, SSH services, and FTP servers.
- **Post-exploitation:** Use compromised credentials to pivot to other services.
- **Internal penetration tests:** Verify that service accounts do not use weak passwords.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed on Kali, Parrot |
| Windows | Limited | Requires Cygwin or WSL |
| macOS | Full | Install via Homebrew |

```bash
# Install on Linux
sudo apt install hydra
```
