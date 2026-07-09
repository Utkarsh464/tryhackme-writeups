# Hydra

## Purpose
Online password brute-forcing tool that supports many protocols (SSH, FTP, HTTP, SMB, MySQL, etc.).

## Installation
```bash
sudo apt install hydra         # Debian/Ubuntu/Kali
```

## Basic Usage
```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://192.168.1.100
hydra -L users.txt -P pass.txt ftp://192.168.1.100
hydra -l admin -P rockyou.txt 192.168.1.100 http-post-form "/login:user=^USER^&pass=^PASS^:F=incorrect"
```

## Important Commands
- `-l LOGIN` — Single username
- `-L FILE` — Username list
- `-p PASSWORD` — Single password
- `-P FILE` — Password list
- `-t N` — Threads (default 16)
- `-V` — Verbose (show each attempt)
- `-f` — Stop on first found
- `-s PORT` — Non-default port
- `http-get` / `http-post-form` — HTTP auth brute-force
- Protocols: `ssh`, `ftp`, `rdp`, `smb`, `mysql`, `vnc`, `pop3`, `smtp`

## Typical Workflow
1. Identify authentication endpoint
2. Prepare wordlists (usernames, passwords)
3. `hydra -l admin -P pass.txt ssh://target`
4. Check protocol syntax: `hydra -U http-post-form` for help
5. Adjust threads: `-t 4` to avoid lockout
6. Use `-f` to stop on first success

## Official Documentation
https://github.com/vanhauser-thc/thc-hydra