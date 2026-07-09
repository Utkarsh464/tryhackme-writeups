# gobuster

**Go Buster** — a tool written in Go for brute-forcing URIs (directories/files), DNS subdomains, and virtual host names.

## Syntax

```
gobuster <mode> [options]
```

## Purpose

Enumerate hidden directories, files, DNS subdomains, and virtual hosts on web servers. Frequently used during web application penetration testing to discover resources not linked from the main site.

## Modes

| Mode | Command | Description |
|------|---------|-------------|
| dir | `gobuster dir` | Directory/file brute-forcing |
| dns | `gobuster dns` | DNS subdomain enumeration |
| vhost | `gobuster vhost` | Virtual host brute-forcing |
| fuzz | `gobuster fuzz` | Fuzzing arbitrary parts of a URL |

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-u` | Target URL (e.g., `http://example.com`) |
| `-w` | Path to wordlist |
| `-t` | Number of threads (default 10) |
| `-x` | File extensions to append (e.g., `-x php,txt,html`) |
| `-s` | Status codes to include (e.g., `-s 200,204,301,302`) |
| `-k` | Skip TLS certificate verification |
| `-r` | Follow redirects |
| `-o` | Output file |
| `-d` | (DNS mode) Domain to enumerate |
| `-n` | (DNS mode) Do not show IP addresses |

## Examples

```bash
# Directory enumeration
gobuster dir -u http://10.10.10.1 -w /usr/share/wordlists/dirb/common.txt

# Directory enumeration with extensions
gobuster dir -u http://10.10.10.1 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt

# DNS subdomain enumeration
gobuster dns -d example.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt

# Virtual host brute-forcing
gobuster vhost -u http://example.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt

# Follow redirects and show only 200/301 responses
gobuster dir -u http://10.10.10.1 -w wordlist.txt -r -s 200,301
```

## Common Mistakes

- Using too many threads (`-t 100`) — can overwhelm the target server or trigger rate limiting.
- Forgetting to add file extensions (`-x`) — you will miss .php, .asp, .jsp pages common on web servers.
- Using tiny wordlists — `common.txt` (only ~4600 entries) often misses important paths. Start small, escalate to larger lists.
- Not following redirects (`-r`) — you may miss pages that redirect to a different path.
- Running without permission — directory brute-forcing can be considered an attack.

## Real-World Usage

- **CTF web challenges:** Find admin panels, backup files, hidden directories, and API endpoints.
- **Penetration testing:** Discover exposed configuration files, database dumps, and version control directories (.git, .svn).
- **Bug bounty:** Uncover hidden functionality in web applications.
- **DNS recon:** Identify subdomains that reveal staging or development environments.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed on Kali, install via `apt install gobuster` |
| Windows | Full | Binary download from GitHub releases |
| macOS | Full | Install via `brew install gobuster` |

```bash
# Install on Linux (Kali/Debian)
sudo apt install gobuster
```
