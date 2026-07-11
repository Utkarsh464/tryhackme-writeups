# Security Principles — Tools

This room is conceptual and does not introduce dedicated security tools. The following categories of tools are referenced in the context of implementing security principles:

## Access Control Tools
- **OpenLDAP / Active Directory:** Directory services that manage authentication and authorization across an organization.
- **sudo / runas:** Privilege elevation tools that enforce least privilege by allowing users to run specific commands with elevated permissions.
- **Fail2ban / CrowdSec:** Tools that monitor authentication logs and block IP addresses after repeated failed login attempts.

## Integrity Verification Tools
- **sha256sum / md5sum / certutil:** Command-line tools for computing file hashes to verify integrity.
- **Tripwire / AIDE:** File integrity monitoring tools that detect unauthorized changes to critical system files.
- **GnuPG / OpenSSL:** Tools for creating and verifying digital signatures.

## Compliance and Audit Tools
- **OpenSCAP:** An automated compliance auditing tool that checks systems against SCAP security baselines.
- **Lynis:** A security auditing tool for Linux systems that performs compliance checks and recommends hardening measures.
- **Microsoft Security Compliance Toolkit:** Tools for managing and auditing GPO-based security settings in Windows environments.
