# Pickle Rick — Tools Reference

## Nmap

- **Purpose**: Port scanning and service/version detection
- **Usage**: Identify the target's listening services before attacking
- **Command**: `sudo nmap -T4 -sV --open 10.48.131.21`

## bustit

- **Purpose**: Async directory brute-forcer for web path enumeration
- **Source**: [github.com/Utkarsh464/dir-brute](https://github.com/Utkarsh464/dir-brute) — my own tool, written in Python with `aiohttp`, installed globally with `uv`
- **Usage**: Feed it a base URL and a wordlist; parallelize with `-t`, print every result with `-v`
- **Command**: `bustit http://10.48.131.21/ /home/l/wordlist/subdirs/web-paths.txt -t 100 -v`

## curl

- **Purpose**: Fetch page source and static endpoints directly from the terminal
- **Usage**: Dump HTML source to find comments, and request `robots.txt`
- **Command**: `curl -s http://10.48.131.21/index.html`
- **Command**: `curl -s http://10.48.131.21/robots.txt`

## Web Browser (Login Portal + Command Panel)

- **Purpose**: Interact with the authenticated web app
- **Usage**:
  - `login.php` — submit `R1ckRul3s` / `Wubbalubbadubdub`
  - `portal.php` — execute commands (this is the foothold)

## sudo

- **Purpose**: Review the current user's elevated privileges
- **Usage**: `sudo -l` in the command panel shows `(ALL) NOPASSWD: ALL` for `www-data`
- **Result**: Every command can run as root without a password — used to read the three ingredient files directly.
