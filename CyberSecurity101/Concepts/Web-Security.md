# Web Security

## Definition
Web security encompasses the practices, technologies, and principles used to protect web applications, web services, and APIs from cyber threats. It addresses vulnerabilities in web application code (injection, broken authentication, XSS), web server configuration, browser security policies (Same-Origin Policy, CORS, CSP), and communication security (HTTPS/TLS).

## Why It Matters
Web applications are the primary attack surface for most organizations. Over 70% of cyberattacks target web applications. A single SQL injection or XSS vulnerability can lead to complete data compromise, account takeover, or malware distribution. Understanding web security is essential for developers (building secure applications), penetration testers (finding vulnerabilities), and defenders (securing infrastructure).

## Where It Appears in the Path
Web security is a major module in the Cyber Security 101 path. It is prerequisite for specific attack categories (SQL injection, XSS, CSRF, SSRF, file inclusion), OWASP Top 10, and web application penetration testing with Burp Suite, ZAP, and other tools.

## Prerequisites
- HTTP/HTTPS fundamentals (methods, status codes, headers, cookies)
- Basic web development concepts (HTML, JavaScript, SQL)
- Networking (DNS, TCP/IP)

## Same-Origin Policy (SOP)
A critical browser security mechanism that restricts how a document or script loaded from one origin can interact with resources from another origin. Two URLs have the same origin if they share the same protocol, host, and port. SOP prevents a malicious website from reading data from another website (e.g., banking site) via the user's browser. Cross-Origin Resource Sharing (CORS) provides controlled exceptions to SOP.

## Input Validation
The practice of validating that user-supplied data conforms to expected formats before processing. Insufficient input validation is the root cause of most web vulnerabilities.

### Client-Side Validation
JavaScript-based validation in the browser. Easy to bypass (turn off JS, intercept requests). NEVER rely solely on client-side validation for security.

### Server-Side Validation
Validation performed on the server after receiving data. Essential for security. Should include:
- **Type checking**: Ensure data types match expected (string, integer, email).
- **Length limits**: Minimum/maximum lengths for strings.
- **Format validation**: Whitelist-based regex patterns (not blacklists).
- **Range validation**: Numeric values within expected bounds.
- **Encoding/Escaping**: Neutralize special characters for the output context (HTML, SQL, JavaScript, URL).

## Authentication & Session Management
- **Weak passwords**: Enforce complexity and MFA.
- **Session hijacking**: Secure cookies (HttpOnly, Secure, SameSite), regenerate session IDs on login.
- **Brute force**: Rate limiting, account lockout, CAPTCHA.
- **Credential stuffing**: Use of compromised credentials across sites (MFA mitigates).
- **Broken authentication** (OWASP Top 10 #7): Logic flaws in authentication flows.

## Access Control
- **Broken Access Control** (OWASP Top 10 #1): Users accessing resources or actions beyond their permissions.
- **IDOR (Insecure Direct Object Reference)**: Accessing resources by manipulating identifiers (e.g., `/user/1234`).
- **Privilege Escalation**: Vertical (user→admin) or horizontal (user→different user).

## Common Vulnerabilities

### SQL Injection
Injecting SQL commands through user input. See SQL Injection.md for comprehensive coverage.

### Cross-Site Scripting (XSS)
Injecting malicious scripts into web pages viewed by other users. See XSS.md for comprehensive coverage.

### Cross-Site Request Forgery (CSRF)
Forces a logged-in user to execute unwanted actions on a web application without their knowledge. Mitigated by anti-CSRF tokens, SameSite cookies, and origin/referer checking.

### Server-Side Request Forgery (SSRF)
Attacker induces the server to make requests to internal resources they cannot directly access. Common in cloud environments (AWS metadata service at 169.254.169.254).

### File Inclusion (LFI/RFI)
Local File Inclusion reads files on the server (e.g., `/etc/passwd`). Remote File Inclusion executes remote files (RCE). Mitigated by whitelist-based inclusion, disable allow_url_include.

### XXE (XML External Entity)
Exploits XML parsers that process external entities. Can read files, perform SSRF, or cause DoS (Billion Laughs attack).

### Insecure Deserialization
Attacker modifies serialized objects (Java, PHP, Python) to execute arbitrary code. Critical vulnerabilities in many frameworks.

## Security Headers
- **Content-Security-Policy (CSP)**: Controls which resources can be loaded and executed. Prevents XSS.
- **X-Content-Type-Options: nosniff**: Prevents MIME type sniffing.
- **X-Frame-Options**: Prevents clickjacking (DENY or SAMEORIGIN).
- **X-XSS-Protection**: Legacy XSS filter (modern browsers deprecating in favor of CSP).
- **Strict-Transport-Security (HSTS)**: Forces HTTPS connections only.
- **Referrer-Policy**: Controls Referer header information leakage.
- **Permissions-Policy**: Controls browser feature access (camera, microphone, geolocation).

## Common Interview Questions
1. **What is the Same-Origin Policy?** Browser security mechanism preventing scripts from one origin from accessing resources from another origin. Defines origin as protocol + host + port.
2. **What is the difference between IDOR and privilege escalation?** IDOR: accessing another user's resource by guessing/manipulating IDs. Privilege escalation: gaining higher permissions than intended.
3. **What is CORS and how does it work?** Cross-Origin Resource Sharing — server uses headers (Access-Control-Allow-Origin) to relax SOP for specific origins. Preflight requests (OPTIONS) check permissions.
4. **What is the difference between session-based and token-based authentication?** Session: server stores session state, client stores session ID in cookie. Token (JWT): client stores token with claims. Token-based is stateless, enables distributed auth.
5. **How would you defend against CSRF?** Anti-CSRF tokens (synchronizer token pattern), SameSite cookies (Strict/Lax), custom headers (X-Requested-By), referer/origin validation.
6. **What is the difference between a WAF and an application firewall?** WAF (Web Application Firewall) is specifically for HTTP/HTTPS traffic — inspects Layer 7 payload (SQL injection, XSS). Application firewall is a broader term for any Layer 7 firewall.

## Further Reading
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security) (free, excellent)
- [Mozilla Web Security](https://infosec.mozilla.org/guidelines/web_security)
- TryHackMe: Web Fundamentals and Web Hacking modules
