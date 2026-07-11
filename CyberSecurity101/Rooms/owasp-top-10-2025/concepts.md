# OWASP Top 10 - 2025 — Concepts

## OWASP Top 10
A regularly updated list of the ten most critical web application security risks, compiled by security experts worldwide through data analysis and community consensus. It serves as an awareness document for developers, security professionals, and organizations to prioritize security investments. The 2025 edition reflects the shift toward API-driven applications, cloud-native architectures, and AI-integrated systems.

## Broken Access Control
Occurs when applications fail to properly enforce user permissions, allowing attackers to access resources or perform actions beyond their authorized scope. Common examples include IDOR (Insecure Direct Object References) where a user modifies a URL parameter to access another user's data, and privilege escalation where a standard user gains administrative functions.

## Injection
A class of vulnerabilities where untrusted data is sent to an interpreter as part of a command or query. SQL injection allows attackers to manipulate database queries. OS command injection allows execution of system commands. NoSQL injection targets MongoDB and similar databases. Template injection exploits server-side template engines. The primary defense is parameterized queries and proper input validation.

## Cryptographic Failures
Formerly "Sensitive Data Exposure," this category focuses on failures in cryptography that lead to compromise of sensitive data. Examples include transmitting data over unencrypted connections, storing passwords with weak hashing algorithms (MD5, SHA1), using outdated ciphers (RC4, DES), and hardcoding encryption keys. Proper solutions include enforced TLS, strong adaptive password hashing (bcrypt, Argon2), and key management best practices.

## SSRF (Server-Side Request Forgery)
A vulnerability where an attacker can induce the server to make HTTP requests to arbitrary destinations chosen by the attacker. SSRF can be used to access internal systems behind firewalls, read cloud instance metadata (e.g., AWS EC2 metadata endpoint at 169.254.169.254), or perform port scans of internal networks. It is particularly dangerous in cloud environments where metadata endpoints contain credentials.

## Software and Data Integrity Failures
A 2025 category encompassing risks related to software supply chain security and insecure deserialization. Attackers compromise software by injecting malicious code into third-party libraries, update mechanisms, or CI/CD pipelines. Insecure deserialization occurs when untrusted data is deserialized without validation, potentially leading to remote code execution. Defenses include signing software artifacts, verifying integrity, and validating serialized data.

## Security Misconfiguration
The most common category on the list, arising from default configurations, incomplete hardening, unnecessary services, misconfigured permissions, and verbose error messages. Each misconfiguration represents an opportunity for attackers. Automation, configuration management tools, and secure baseline templates (e.g., CIS benchmarks) are key defenses.
