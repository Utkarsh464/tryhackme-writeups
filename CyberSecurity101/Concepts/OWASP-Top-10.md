# OWASP Top 10

## Definition
The OWASP Top 10 is a standard awareness document published by the Open Web Application Security Project (OWASP) that represents a consensus on the most critical security risks to web applications. Updated approximately every 3-4 years, the Top 10 categorizes and prioritizes web vulnerabilities based on prevalence, exploitability, detectability, and technical/business impact. The latest version is 2021.

## Why It Matters
The OWASP Top 10 is the de facto standard for web application security awareness. It guides security policies, secure coding standards, penetration testing scopes, and compliance frameworks (PCI DSS references OWASP Top 10). For developers, it identifies what to avoid. For penetration testers, it defines the minimum test coverage. For organizations, it provides a risk-based prioritization of security investments.

## Where It Appears in the Path
The OWASP Top 10 is covered in the web security module. It synthesizes knowledge from earlier topics (SQL injection, XSS, broken authentication, insecure deserialization) and introduces broader vulnerability categories. It is essential for anyone doing web application security assessments.

## Prerequisites
- Web application fundamentals (HTTP, sessions, cookies, authentication)
- Understanding of common vulnerabilities (SQLi, XSS, CSRF)
- Basic risk assessment concepts

## OWASP Top 10 — 2021

### A01 — Broken Access Control
**Description**: Failures in enforcing user permissions — users can access resources or perform actions beyond their authorized level. Includes Insecure Direct Object References (IDOR), missing access controls on APIs, forced browsing, and privilege escalation.
**Prevalence**: Moved from #5 to #1 in 2021. Present in 94% of applications tested.
**Prevention**: Consistent access control checks on the server, deny-by-default, implement least privilege, use role-based access control (RBAC), disable directory listing, log access control failures.

### A02 — Cryptographic Failures
**Description**: Failures related to protecting data in transit and at rest. Formerly "Sensitive Data Exposure". Includes weak encryption algorithms (DES, RC4, MD5), missing HTTPS, weak SSL/TLS configurations, exposed passwords, and predictable random numbers.
**Prevention**: Encrypt all sensitive data at rest (AES-256) and in transit (TLS 1.2+). Use strong up-to-date ciphers. Hash passwords with Argon2/bcrypt/scrypt. Disable caching for sensitive data.

### A03 — Injection
**Description**: User-supplied data sent to an interpreter as part of a command or query. Includes SQL injection, NoSQL injection, OS command injection, LDAP injection, and XSS (injection into HTML/JavaScript). SQL injection specifically remains the most damaging injection type.
**Prevention**: Parameterized queries (prepared statements), ORM frameworks, input validation (whitelist), escape special characters, least privilege database accounts.

### A04 — Insecure Design
**Description**: New category in 2021 focusing on design flaws rather than implementation bugs. Includes missing threat modeling, unvalidated access control assumptions, insecure business logic flows, and missing rate limiting.
**Prevention**: Threat modeling during design phase, secure design patterns, reference architectures, security requirements in user stories, abuse case testing.

### A05 — Security Misconfiguration
**Description**: Missing security hardening across the application stack — unpatched systems, default credentials, unnecessary services enabled, directory listing enabled, verbose error messages, misconfigured CORS headers, missing security headers.
**Prevention**: Automated hardening processes, minimal platform configuration, regular vulnerability scanning, disable unnecessary features, strong default-deny policies, immutable infrastructure.

### A06 — Vulnerable and Outdated Components
**Description**: Using components (libraries, frameworks, software) with known vulnerabilities. Includes using old versions with known CVEs, not scanning for vulnerabilities, and unsupported/end-of-life software. The Equifax breach was caused by an unpatched Apache Struts vulnerability.
**Prevention**: Software Composition Analysis (SCA), keep dependencies updated, monitor CVEs (NVD, OWASP Dependency-Check), use only maintained components, remove unused dependencies.

### A07 — Identification and Authentication Failures
**Description**: Weak authentication mechanisms — allows credential stuffing, brute force, session hijacking, weak password policies, exposed session IDs in URLs, session fixation, and missing MFA.
**Prevention**: MFA/2FA, strong password policies, rate limiting on login, secure session management (HttpOnly, Secure, SameSite cookies, regenerate on login), credential stuffing detection (device fingerprinting).

### A08 — Software and Data Integrity Failures
**Description**: Failures related to trusting software updates, CI/CD pipelines, and unsigned data. Includes supply chain attacks (SolarWinds), insecure deserialization, unsigned software updates, and malicious packages in registries (npm typosquatting, PyPI malware).
**Prevention**: Sign code and artifacts, verify software integrity, use secure CI/CD pipelines, dependency integrity verification, use package lock files, artifact hashes.

### A09 — Security Logging and Monitoring Failures
**Description**: Insufficient logging, monitoring, and alerting so that breaches go undetected. Includes missing audit logs, unclear log messages, no centralized logging, no alerting on suspicious events, and logs not retaining for sufficient periods.
**Prevention**: Log all authentication events, access control failures, input validation failures, and server-side errors. Centralize logs with SIEM. Implement real-time alerting. Retain logs as per compliance.

### A10 — Server-Side Request Forgery (SSRF)
**Description**: Added in 2021. An attacker can induce the server to make requests to arbitrary URLs, bypassing access controls. Critical in cloud environments where metadata services (AWS 169.254.169.254) provide credentials.
**Prevention**: Validate and whitelist allowed URLs and IP ranges, block access to private IP ranges (127.0.0.0/8, 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16, 169.254.169.254), disable unnecessary URL schemes (file://), network segmentation.

## Common Interview Questions
1. **What is the OWASP Top 10?** A list of the ten most critical web application security risks, published by OWASP. Updated every 3-4 years.
2. **What is the #1 risk in the OWASP Top 10 2021?** Broken Access Control (A01) — moved from #5.
3. **How has the OWASP Top 10 changed between 2017 and 2021?** Insecure Design (A04) and SSRF (A10) were added. Cryptographic Failures replaced Sensitive Data Exposure. Injection dropped from #1 to #3. Cross-Site Scripting was folded into Injection.
4. **What is the most common web vulnerability according to OWASP?** Broken Access Control (94% of tested applications).
5. **How would you remediate injection vulnerabilities?** Parameterized queries, input validation, least privilege database accounts, and WAF for defense-in-depth.
6. **Why is SSRF particularly dangerous in cloud environments?** Cloud metadata services (AWS IMDS at 169.254.169.254) expose instance credentials. SSRF can leak cloud credentials and compromise the entire cloud infrastructure.

## Further Reading
- [OWASP Top 10 2021 Official Page](https://owasp.org/www-project-top-ten/)
- [OWASP Top 10 Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/OWASP_Top_Ten_Cheat_Sheet.html)
- [OWASP ASVS (Application Security Verification Standard)](https://owasp.org/www-project-application-security-verification-standard/)
- [CWE (Common Weakness Enumeration)](https://cwe.mitre.org/)
- TryHackMe: OWASP Top 10 room
