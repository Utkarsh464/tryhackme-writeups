# Dirb

## Purpose
Dirb (Directory Buster) is a URL content scanner that performs dictionary-based attacks against web servers to discover hidden directories and files. It is one of the oldest and most well-known web content discovery tools in the penetration testing community. Dirb works by sending HTTP requests to a target web server using words from a dictionary file, identifying valid resources based on HTTP response codes. While slower than modern alternatives like Gobuster, Dirb remains a reliable tool with broad platform support.

## Installation
```bash
# Kali Linux (pre-installed)
dirb

# Debian/Ubuntu
sudo apt update && sudo apt install dirb

# Arch Linux
sudo pacman -S dirb

# macOS
brew install dirb

# Build from source
git clone https://github.com/oblique/dirb
cd dirb
./configure && make && sudo make install

# Windows
# Download ZIP from SourceForge or GitHub releases
# Run dirb.exe from command prompt
```

## Basic Usage
```bash
# Simple directory scan
dirb http://targetsite.com

# Scan with custom wordlist
dirb http://targetsite.com /usr/share/wordlists/dirb/big.txt

# Scan with file extensions
dirb http://targetsite.com -X .php,.html,.txt

# Scan with SSL
dirb https://targetsite.com
```

## Important Options
- `-a <agent>` - set custom User-Agent string
- `-b` - don't show empty HTTP 404 pages (suppress 404 body)
- `-c <cookie>` - set HTTP cookies (e.g., `-c "PHPSESSID=abc123"`)
- `-E <cert>` - specify client SSL certificate file (PEM format)
- `-f` - fine-tune not-found detection (check 404 response page)
- `-H <header>` - add custom HTTP header (e.g., `-H "Authorization: Basic base64"`)
- `-i` - show only HTTP 200 responses (invert filter)
- `-l` - display verbose output with full URLs and status codes
- `-N <code>` - ignore responses with specified HTTP code (e.g., `-N 403`)
- `-o <file>` - write output to file
- `-p <proxy:port>` - use HTTP proxy
- `-P <protocol>` - proxy authentication (e.g., `-P http://user:pass@proxy:port`)
- `-r` - don't recursively scan directories
- `-R` - interactive mode (ask before each request)
- `-S` - silent mode (only display found results)
- `-t` - don't force trailing `/` on URL
- `-u <user:pass>` - HTTP basic authentication
- `-v` - show all responses (including not-found)
- `-w` - display warning messages
- `-x <ext>` - file extensions with leading dot (e.g., `.php,.asp,.txt`)
- `-X <ext>` - same as `-x` but without leading dot (e.g., `php,asp,txt`)
- `-z <ms>` - delay between requests in milliseconds

## Wordlists Included
Dirb ships with several wordlists located in `/usr/share/dirb/wordlists/`:
- `common.txt` - Common directories and files (about 4,600 entries)
- `big.txt` - Larger wordlist (about 20,000 entries)
- `small.txt` - Minimal wordlist for quick scans
- `extensions_common.txt` - File extensions list
- `mutations_common.txt` - Path mutation patterns
- `vulns/apache.txt` - Apache-specific paths
- `vulns/iis.txt` - IIS-specific paths
- `vulns/tomcat.txt` - Tomcat-specific paths
- `vulns/cgis.txt` - CGI script paths

## Typical Workflow
1. Identify web server from Nmap scan results (port 80, 443, 8080, etc.)
2. Run Dirb with the `common.txt` wordlist for initial discovery: `dirb http://target.com`
3. If the server uses file extensions, add `-X` flag with relevant extensions
4. For more thorough scanning, use the `big.txt` wordlist: `dirb http://target.com /usr/share/dirb/wordlists/big.txt`
5. Review output for interesting paths (admin panels, backups, configuration files)
6. Verify discovered paths manually in a browser
7. If authentication is required, use `-u` or `-c` flags
8. Recursively scan interesting subdirectories found during the initial scan
9. Cross-reference findings with other enumeration tools (Nikto, Gobuster, Nmap)

## Advantages
- Pre-installed on Kali and most security distributions
- Simple and intuitive syntax easy for beginners
- Multiple wordlists included for various scan depths
- SSL/TLS support out of the box
- Proxy support for integration with other tools
- Customizable HTTP headers for authentication
- No dependencies beyond Perl (cross-platform)
- Silent and verbose modes for different use cases

## Limitations
- Single-threaded and significantly slower than Gobuster or FFUF
- No DNS subdomain enumeration mode
- No virtual host enumeration
- Recursive scanning must be manually configured
- No built-in content-length filtering
- Perl dependency can cause issues on some systems
- Less actively maintained than alternatives
- Output formatting is basic and harder to parse programmatically

## Industry Use
Dirb is used by penetration testers and security students as an introductory web enumeration tool. It is commonly found in CTF walkthroughs and TryHackMe rooms for simple directory discovery. While many professionals have migrated to faster tools like Gobuster or FFUF, Dirb remains relevant for legacy systems and basic use cases.

## Official Documentation
- GitHub: https://github.com/oblique/dirb
- Kali Docs: https://www.kali.org/tools/dirb/
- Wordlists: `/usr/share/dirb/wordlists/`
- Manual: `man dirb`
- SourceForge: https://sourceforge.net/projects/dirb/
