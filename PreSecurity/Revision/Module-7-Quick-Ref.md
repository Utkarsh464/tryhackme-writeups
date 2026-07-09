# Module 7: Attacks and Defenses — Quick Reference

## Key Concepts
- **CIA Triad Review**: Confidentiality (encryption, access control), Integrity (hashing, digital signatures), Availability (redundancy, DDoS protection)
- **Hashing**: One-way, deterministic, collision-resistant (SHA-256, bcrypt)
- **Symmetric Encryption**: Same key for encrypt/decrypt (AES, ChaCha20)
- **Asymmetric Encryption**: Public/private key pair (RSA, ECC, ECDH)
- **Digital Signatures**: Sign with private key, verify with public key
- **PKI**: Certificate Authorities, TLS certificates, trust chains
- **Cyber Kill Chain**: Recon → Weaponize → Deliver → Exploit → Install → C2 → Actions
- **MITRE ATT&CK**: Knowledge base of adversary tactics and techniques based on real-world observations
- **Incident Response**: Detection → Analysis → Containment → Eradication → Recovery → Lessons Learned

## Types of Attacks
| Attack | Description |
|--------|-------------|
| Phishing | Fraudulent emails/sites to steal credentials |
| Malware | Viruses, worms, trojans, ransomware |
| DDoS | Overwhelm server with traffic |
| MITM | Intercepting communication |
| SQL Injection | Injecting malicious SQL |
| XSS | Injecting malicious scripts into web pages |
| CSRF | Forging authenticated requests |
| Brute Force | Trying all password combinations |
| Social Engineering | Manipulating people to reveal info |
| Password Spraying | Trying common passwords across many accounts |

## Key Defenses
| Defense | Purpose |
|---------|---------|
| Firewall | Filters network traffic |
| IDS/IPS | Detects/prevents intrusions |
| Antivirus/EDR | Endpoint protection |
| SIEM | Centralized log analysis and alerting |
| MFA | Multi-factor authentication |
| Encryption | Protects data confidentiality |
| Backups | Enables recovery from ransomware/disaster |
| Patch Management | Fixes known vulnerabilities |
| Security Awareness Training | Educates users against phishing/social engineering |
| Principle of Least Privilege | Minimizes damage from compromise |

## Key Terms
- **Threat Actor**: Individual/group behind an attack
- **APT**: Advanced Persistent Threat — state-sponsored, long-term
- **IoC**: Indicator of Compromise — evidence of intrusion
- **TTP**: Tactics, Techniques, and Procedures — attacker behavior
- **SOC**: Security Operations Center — monitors and responds
- **SOAR**: Security Orchestration, Automation and Response
- **XDR**: Extended Detection and Response — cross-layer threat detection
