# Concepts: Operating System Security

## 1. Least Privilege
Every user, process, or system component should have only the minimal permissions necessary. Applying least privilege reduces damage from compromised accounts, limits malware impact, and narrows the attack surface.

## 2. Authentication Factors
Knowledge factors (passwords) are widely used but vulnerable. Possession factors (hardware tokens, phone) are harder to steal remotely. Inherence factors (fingerprint, face) provide convenience. MFA combining two factors dramatically increases security.

## 3. Password Policies
Minimum length (12+ chars), complexity requirements, maximum age, and account lockout. Modern guidance favours long passphrases over complex short passwords with frequent rotation.

## 4. Patch Management
Identifying, acquiring, testing, and installing security updates. Patches fix known vulnerabilities actively exploited by attackers. Delaying patches increases the window of exposure.

## 5. Security Logging
Recording login attempts, privilege use, file access, and policy changes. Windows Security Logs track these events. Linux auditd provides detailed audit trails. Logs should be centralised via SIEM and protected from tampering.

## 6. Host-Based Firewall
Software firewall on endpoints filtering incoming/outgoing traffic. Blocks unauthorised connections, restricts services to specific IPs, and prevents malware from phoning home.

## 7. Disabling Unnecessary Services
Every running service is a potential entry point. Disabling unneeded services (Telnet, FTP, SMBv1, print spooler) reduces the attack surface. This is the foundation of system hardening.

## 8. Application Whitelisting vs Blacklisting
Whitelisting allows only approved applications to run (default-deny). Blacklisting blocks known malicious applications (default-allow). Whitelisting is far more secure. Enforced via Windows AppLocker, Software Restriction Policies, or SELinux/apparmor.