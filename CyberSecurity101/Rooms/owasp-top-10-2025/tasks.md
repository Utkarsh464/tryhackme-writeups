# OWASP Top 10 - 2025 — Tasks

## Task 1: Introduction to OWASP Top 10 2025
Learn about the OWASP organization and the purpose of the Top 10 list. Understand how the 2025 edition differs from previous editions, including new categories related to AI threats, API security, and supply chain risks. Review the methodology used to compile the list.

## Task 2: A01 — Broken Access Control
Exploit a broken access control vulnerability by manipulating URL parameters, HTTP headers, or cookies to access resources that should be restricted. Learn about IDOR (Insecure Direct Object References), privilege escalation, and missing function-level access controls. Implement proper access control checks and use role-based permissions to remediate.

## Task 3: A02 — Cryptographic Failures
Identify pages transmitting sensitive data over HTTP instead of HTTPS. Exploit weak password storage by cracking unsalted MD5 hashes. Use Burp Suite to intercept and inspect traffic for exposed credit card numbers, session tokens, or passwords in cleartext. Remediate by enforcing TLS, using strong adaptive hashing (bcrypt, Argon2), and encrypting sensitive data at rest.

## Task 4: A03 — Injection
Exploit SQL injection by bypassing authentication forms and extracting data from the database using UNION-based and blind SQL injection techniques. Learn to automate the process with SQLMap. Also explore NoSQL injection, OS command injection, and template injection (SSTI). Remediate by using parameterized queries, input validation, and proper escaping.

## Task 5: A04 — Insecure Design
Identify design-level flaws such as missing rate limiting on login forms, insecure password reset workflows, and lack of access control reviews. Understand that these flaws cannot be fixed with code alone — they require secure design patterns, threat modeling, and security requirements in the design phase.

## Task 6: A05 — Security Misconfiguration
Discover security misconfigurations including default credentials, directory listing enabled, unnecessary services running, verbose error messages exposing stack traces, and missing security headers. Remediate by hardening configurations, automating configuration reviews, and using secure baseline templates.

## Task 7: A06 — Vulnerable and Outdated Components
Identify outdated libraries and frameworks by examining response headers, client-side JavaScript, and known CVE databases. Learn about dependency scanning tools (OWASP Dependency-Check, Snyk). Remediate by maintaining an inventory of components, applying patches promptly, and removing unused dependencies.

## Task 8: A07 — Identification and Authentication Failures
Exploit weak authentication mechanisms: brute force login pages, session fixation, and weak password policies. Understand MFA bypass techniques. Remediate by enforcing strong password policies, implementing account lockout, using MFA, and setting secure session management configurations.

## Task 9: A08 — Software and Data Integrity Failures
Understand supply chain attacks where malicious code is introduced through compromised dependencies or CI/CD pipelines. Explore insecure deserialization vulnerabilities where untrusted data is deserialized without validation. Remediate by verifying software signatures, using signed commits, and validating all serialized objects.

## Task 10: A09 — Security Logging and Monitoring Failures
Identify the absence of logging in critical application functions such as authentication attempts and administrative actions. Learn what should be logged (timestamps, user IDs, source IPs, actions) and what should not (passwords, credit card numbers). Understand how proper logging enables incident detection and forensic investigation.

## Task 11: A10 — Server-Side Request Forgery (SSRF)
Exploit SSRF by crafting requests that trick the server into making internal network requests, potentially accessing cloud metadata endpoints, internal services, or local files. Understand how SSRF can lead to remote code execution in cloud environments. Remediate by validating URLs, blocking internal IP ranges, and using allow lists.

## Task 12: Final Assessment Challenge
A comprehensive challenge that combines multiple OWASP Top 10 categories. Apply everything learned in this room and across the Cyber Security 101 path to identify, exploit, and remediate vulnerabilities in a realistic web application. Document your findings and proposed fixes.
