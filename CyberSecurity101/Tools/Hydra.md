# Hydra

## Purpose
Hydra (THC-Hydra) is a massively parallel network login cracker developed by The Hackers Choice (THC). It performs rapid brute-force attacks against network services to discover valid credentials. Hydra supports numerous protocols including SSH, FTP, HTTP/S, SMB, MySQL, PostgreSQL, RDP, VNC, SMTP, POP3, IMAP, LDAP, and many more. It is one of the fastest and most flexible online password attack tools available.

## Installation
Hydra is pre-installed on Kali Linux. For other systems:
```bash
# Debian/Ubuntu
sudo apt update && sudo apt install hydra

# Red Hat/CentOS/Fedora
sudo dnf install hydra

# Arch Linux
sudo pacman -S hydra

# macOS
brew install hydra

# Build from source
git clone https://github.com/vanhauser-thc/thc-hydra
cd thc-hydra && ./configure && make && sudo make install
```

## Basic Usage
Hydra requires a target, protocol, and credential options:
```bash
# SSH brute-force
hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://10.10.10.10

# FTP brute-force with username list
hydra -L usernames.txt -P passwords.txt ftp://10.10.10.10

# HTTP POST form brute-force
hydra -l admin -P pass.txt 10.10.10.10 http-post-form "/login:user=^USER^&pass=^PASS^:Invalid"
```

## Important Options
- `-l <login>` - single username to try
- `-L <file>` - file containing multiple usernames
- `-p <password>` - single password to try
- `-P <file>` - file containing multiple passwords
- `-t <num>` - number of parallel tasks (threads)
- `-f` / `-F` - stop after first found user/password pair
- `-v` / `-V` - verbose mode / show each login attempt
- `-o <file>` - write found credentials to file
- `-s <port>` - specify non-default port
- `-e nsr` - try null password, login as password, reverse login
- `-M <file>` - list of targets (one per line)
- `-w <time>` - wait time between requests (seconds)
- `-W <time>` - time between connections
- `-I` - ignore restores from previous sessions
- `-u` - loop around users, not passwords (cycling mode)

## Supported Protocols (partial list)
`adam6500, afp, asterisk, cisco, cisco-enable, cvs, firebird, ftp, ftps, http-get, http-post, http-get-form, http-post-form, http-proxy, imap, irc, ldap2, ldap3, mssql, mysql, nntp, oracle, oracle-listener, oracle-sid, pcanywhere, pcnfs, pop3, postgres, rdp, redis, rexec, rlogin, rpcap, rsh, rtsp, s7-300, sip, smb, smtp, smtp-enum, snmp, socks5, ssh, sshkey, svn, teamspeak, telnet, tds, vnc, xmpp`

## Typical Workflow
1. Identify an open service from Nmap scan (e.g., SSH on port 22, FTP on port 21)
2. Determine the target username through OSINT or common defaults
3. Select an appropriate password wordlist (RockYou for general targets, custom lists from OSINT)
4. Configure Hydra with the target, service module, and credential options
5. Start with a quick test using a small wordlist to verify syntax
6. Run the full attack with appropriate thread count (start conservative, increase gradually)
7. Record discovered credentials and test them against other services
8. Use the -f flag to stop Hydra as soon as valid credentials are found

## Advantages
- Extremely fast parallelized attack engine (supports hundreds of concurrent connections)
- Supports more protocols than any competing tool (50+ protocol modules)
- Highly configurable thread count and timing controls
- Modular protocol architecture allows easy addition of new services
- IPv6 support across all protocols
- Can pause and resume sessions
- Proxy support for multi-hop attacks

## Limitations
- Online attacks generate detectable network traffic
- Lockout policies can disable accounts after failed attempts
- No built-in distributed attack capabilities (use Hydra in parallel manually)
- Form brute-force requires manual analysis of response strings
- No built-in proxy rotation or IP spoofing
- Cannot bypass CAPTCHA or MFA
- Success depends entirely on wordlist quality

## Industry Use
Hydra is used in penetration testing to test account lockout policies, by red teams to gain initial access, by security auditors to validate password policies, and by incident responders who need to recover access to locked accounts. It is a standard tool in any credential-testing workflow.

## Official Documentation
- GitHub: https://github.com/vanhauser-thc/thc-hydra
- Official Site: https://www.thc.org/thc-hydra/
- Kali Docs: https://www.kali.org/tools/hydra/
- Manual: `man hydra`
