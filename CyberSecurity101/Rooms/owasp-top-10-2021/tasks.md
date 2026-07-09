# OWASP Top 10 - 2021 - Tasks

## Task 1: Introduction to OWASP Top 10
- Understand what OWASP is and its role in web security
- Learn about the methodology and data sources for the Top 10
- Compare the 2021 edition with the 2017 edition
- Understand how to use the OWASP Top 10 as a security reference

## Task 2: A01 - Broken Access Control
- Understand what access control is and why it matters
- Learn about Insecure Direct Object References (IDOR)
- Practice privilege escalation by modifying user roles
- Explore path traversal and forced browsing vulnerabilities
- Learn mitigation: role-based access control, deny-by-default

## Task 3: A02 - Cryptographic Failures
- Understand what constitutes a cryptographic failure
- Identify sensitive data exposure in transit (HTTP vs HTTPS)
- Identify sensitive data exposure at rest (weak encryption)
- Learn about improper TLS/SSL configuration
- Practice extracting data from improperly encrypted sources
- Learn mitigation: strong encryption, proper key management

## Task 4: A03 - Injection
- Understand injection vulnerabilities and how they work
- Practice SQL injection to bypass authentication
- Use UNION-based injection to extract data from other tables
- Explore NoSQL injection and command injection
- Learn mitigation: parameterized queries, input validation

## Task 5: A04 - Insecure Design
- Understand the difference between insecure design and insecure implementation
- Learn about threat modeling and secure design principles
- Identify design flaws that lead to security vulnerabilities
- Explore rate limiting failures and business logic flaws
- Learn mitigation: secure design patterns, security requirements

## Task 6: A05 - Security Misconfiguration
- Understand common misconfiguration categories
- Identify default credentials and unnecessary services
- Explore directory listing and information disclosure
- Learn about improper HTTP headers and CORS misconfiguration
- Learn mitigation: hardening guides, automated configuration reviews

## Task 7: A06 - Vulnerable and Outdated Components
- Understand the risk of using outdated software components
- Learn about software composition analysis and dependency management
- Identify outdated components in web applications
- Explore known vulnerability databases (CVE, NVD)
- Learn mitigation: regular updates, vulnerability scanning, component inventory

## Task 8: A07 - Identification and Authentication Failures
- Understand authentication mechanisms and their weaknesses
- Practice brute-forcing login forms
- Explore session fixation, session hijacking, and weak session tokens
- Learn about multi-factor authentication bypass
- Learn mitigation: strong password policies, MFA, secure session management

## Task 9: A08 - Software and Data Integrity Failures
- Understand integrity failures in software and data
- Learn about insecure deserialization
- Explore supply chain attacks in CI/CD pipelines
- Understand how auto-update mechanisms can be exploited
- Learn mitigation: code signing, integrity checks, secure build pipelines

## Task 10: A09 - Security Logging and Monitoring Failures
- Understand the importance of logging and monitoring
- Identify insufficient logging configurations
- Learn about log injection and log forging
- Explore how monitoring failures enable prolonged attacks
- Learn mitigation: comprehensive logging, SIEM integration, alerting

## Task 11: A10 - Server-Side Request Forgery (SSRF)
- Understand how SSRF attacks work
- Exploit SSRF to access internal resources
- Use SSRF to interact with cloud metadata endpoints
- Learn about blind SSRF and out-of-band detection
- Learn mitigation: input validation, allow-list-based filtering, network segmentation

## Task 12: Conclusion and Final Challenge
- Review all OWASP Top 10 categories
- Complete a final challenge combining multiple vulnerabilities
- Understand how to apply OWASP Top 10 in professional assessments
- Prepare for advanced web security topics
