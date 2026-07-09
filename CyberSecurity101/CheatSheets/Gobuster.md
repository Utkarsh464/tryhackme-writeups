# Gobuster Cheat Sheet

## Basic Syntax
```bash
gobuster <mode> [options]
```

## Dir Mode (Directory/File Brute-Forcing)
| Command | Description |
|---------|-------------|
| `gobuster dir -u http://target.com -w wordlist.txt` | Basic dir bust |
| `gobuster dir -u http://target.com -w wordlist.txt -x php,txt,html` | Add extensions |
| `gobuster dir -u http://target.com -w wordlist.txt -x php -e` | Include full URL in output |
| `gobuster dir -u http://target.com -w wordlist.txt -t 50` | Threads (default 10) |
| `gobuster dir -u http://target.com -w wordlist.txt -s 200,204,301,302,307,403` | Status codes to match |
| `gobuster dir -u http://target.com -w wordlist.txt -b 404` | Exclude 404 |
| `gobuster dir -u http://target.com -w wordlist.txt -c "session=abc123"` | Cookie |
| `gobuster dir -u http://target.com -w wordlist.txt -H "Header: value"` | Custom header |
| `gobuster dir -u http://target.com -w wordlist.txt -U admin -P pass` | Basic auth |
| `gobuster dir -u http://target.com -w wordlist.txt -k` | Skip TLS verification |
| `gobuster dir -u http://target.com -w wordlist.txt -r` | Follow redirects |
| `gobuster dir -u http://target.com -w wordlist.txt -f` | Append `/` to dirs |
| `gobuster dir -u http://target.com -w wordlist.txt -n` | No status codes |
| `gobuster dir -u http://target.com -w wordlist.txt -l` | Show response length |
| `gobuster dir -u http://target.com -w wordlist.txt -o output.txt` | Save to file |

## DNS Mode (Subdomain Enumeration)
| Command | Description |
|---------|-------------|
| `gobuster dns -d target.com -w subdomains.txt` | Basic DNS enum |
| `gobuster dns -d target.com -w subdomains.txt -t 50` | Threads |
| `gobuster dns -d target.com -w subdomains.txt -i` | Show IP addresses |
| `gobuster dns -d target.com -w subdomains.txt -r 8.8.8.8` | Custom DNS server |
| `gobuster dns -d target.com -w subdomains.txt -c` | Show CNAME records |
| `gobuster dns -d target.com -w subdomains.txt -o output.txt` | Save results |
| `gobuster dns -d target.com -w subdomains.txt -b "NXDOMAIN"` | Exclude status |

## Vhost Mode (Virtual Host Enumeration)
| Command | Description |
|---------|-------------|
| `gobuster vhost -u http://target.com -w vhosts.txt` | Vhost brute force |
| `gobuster vhost -u http://target.com -w vhosts.txt -t 30` | Threads |
| `gobuster vhost -u http://target.com -w vhosts.txt -k` | Skip TLS |
| `gobuster vhost -u http://target.com -w vhosts.txt -e` | Extended mode |
| `gobuster vhost -u http://target.com -w vhosts.txt -c "cookie=val"` | Cookie |

## Common Options
| Flag | Description |
|------|-------------|
| `-t 10` | Concurrency threads |
| `-o file` | Output file |
| `-q` | Quiet mode |
| `-w wordlist` | Path to wordlist |
| `-z` | No progress updates |

## Extensions
| Extension | Purpose |
|-----------|---------|
| `-x php` | PHP files |
| `-x php,txt,html` | Multiple extensions |
| `-x asp,aspx` | ASP/ASP.NET |
| `-x jsp,do` | Java |
| `-x js,json,xml` | Data files |
| `-x bak,old,save` | Backup files |

## Throttling & Performance
```bash
# Slow and stealthy
gobuster dir -u http://target.com -w wordlist.txt -t 5 -q

# Fast (good network)
gobuster dir -u http://target.com -w wordlist.txt -t 100

# Balanced
gobuster dir -u http://target.com -w wordlist.txt -t 50 -o results.txt
```

## Wordlist Recommendations
| Wordlist | Usage |
|----------|-------|
| `/usr/share/wordlists/dirb/common.txt` | Quick, small |
| `/usr/share/wordlists/dirb/big.txt` | Medium coverage |
| `/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt` | Thorough |
| `/usr/share/wordlists/SecLists/Discovery/Web-Content/raft-large-files.txt` | Raft files |
| `/usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt` | DNS top 5000 |
| `/usr/share/wordlists/SecLists/Discovery/Web-Content/big.txt` | Web content |

## Examples
```bash
# Web directory scan
gobuster dir -u http://10.10.10.1 -w /usr/share/wordlists/dirb/common.txt -x php,html,txt -t 50 -o web_scan.txt

# Subdomain enum
gobuster dns -d example.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -i

# Vhost discovery
gobuster vhost -u http://example.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -t 30

# Quick check with cookie auth
gobuster dir -u http://target.com/dashboard -w wordlist.txt -c "PHPSESSID=abc123" -t 20
```
