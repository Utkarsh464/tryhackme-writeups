# Penetration Testing Foundations — Study Notes

## Pentesting Fundamentals

### Pentest Stages
1. **Information Gathering** — OSINT, public data, passive recon
2. **Enumeration/Scanning** — Active recon, port scanning, service discovery
3. **Exploitation** — Gaining access via identified vulns
4. **Privilege Escalation** — Moving from limited to full access
5. **Post-Exploitation** — Persistence, data exfiltration, pivoting
6. **Reporting** — Document findings, recommendations, executive summary

### Testing Types
- **Black Box** — No prior knowledge of the target
- **Grey Box** — Limited knowledge (some credentials, architecture docs)
- **White Box** — Full knowledge (source code, credentials, network maps)

### Methodologies
- OSSTMM — Telecom-focused testing framework
- OWASP — Web application security testing
- NIST CSF — Organisational cybersecurity framework
- NCSC CAF — UK-focused cyber assessment framework

### Rules of Engagement (ROE)
- Defines scope, boundaries, and permissions
- Signed before any testing begins
- Includes: timeline, targets, allowed techniques, data handling

## Principles of Security

### CIA Triad
- **Confidentiality** — Only authorised users can access data
- **Integrity** — Data cannot be altered by unauthorised parties
- **Availability** — Data and systems are accessible when needed

### Privilege Management
- **PIM** (Privileged Identity Management) — Managing who has privileges
- **PAM** (Privileged Access Management) — Managing what privileges allow

### Security Models
- **Bell-LaPadula** — Military model: no read up, no write down (focus on confidentiality)
- **Biba** — Integrity model: no read down, no write up (focus on data integrity)

### Threat Modelling — STRIDE
- **S**poofing — Impersonating someone/something
- **T**ampering — Modifying data without authorisation
- **R**epudiation — Denying actions
- **I**nformation Disclosure — Exposing private data
- **D**enial of Service — Disrupting service availability
- **E**levation of Privilege — Gaining unauthorised access

### Incident Response
1. Preparation
2. Detection & Analysis
3. Containment, Eradication & Recovery
4. Post-Incident Activity
