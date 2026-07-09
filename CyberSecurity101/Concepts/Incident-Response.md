# Incident Response

## Definition
Incident Response (IR) is the systematic approach to managing and resolving cybersecurity incidents. An IR plan outlines the processes, procedures, and tools an organization uses to detect, contain, eradicate, and recover from security events. The goal is to minimize damage, reduce recovery time, manage incident costs, and preserve evidence for legal proceedings.

## Why It Matters
Every organization will face security incidents — it's not a matter of if, but when. A well-defined IR process can mean the difference between a minor inconvenience and a catastrophic data breach costing millions. Effective IR reduces dwell time (the period attackers remain undetected), limits data loss, maintains customer trust, and meets regulatory requirements (GDPR 72-hour notification, PCI DSS incident response plan mandate, HIPAA breach notification).

## Where It Appears in the Path
Incident response is a core defensive/blue team topic. It integrates knowledge from digital forensics (evidence collection), networking (traffic analysis), SIEM (detection), malware analysis (understanding threats), and system administration (containment and recovery).

## Prerequisites
- Networking fundamentals
- Operating system administration
- Digital forensics basics
- Understanding of common attack vectors

## The Incident Response Lifecycle

### 1. Preparation
The most critical phase. Organizations must be ready before an incident occurs:
- Develop and maintain an Incident Response Plan (IRP)
- Assemble an Incident Response Team (IRT/CIRT/CSIRT)
- Acquire and maintain IR tools (forensic workstations, write-blockers, analysis software)
- Implement logging, monitoring, and alerting infrastructure
- Conduct regular tabletop exercises and simulations
- Establish communication plans (internal, legal, PR, law enforcement)
- Create system baselines and known-good backups

### 2. Detection & Analysis
Identify that an incident may be occurring:
- **Indicators of Compromise (IOCs)**: IP addresses, domains, file hashes, registry keys, process names
- **Indicators of Attack (IOAs)**: Behavioral patterns indicating active attack (lateral movement, privilege escalation)
- **Sources**: SIEM alerts, EDR alerts, firewall logs, IDS/IPS alerts, antivirus detections, user reports, threat intelligence feeds, anomalous network traffic
- **Triage**: Determine severity (Low/Medium/High/Critical), impact, and scope
- **Documentation**: Log every action, finding, and decision with timestamps

### 3. Containment
Stop the incident from spreading and causing further damage:
- **Short-term**: Isolate affected systems (disconnect network cables, disable NICs, create firewall ACLs)
- **Long-term**: Apply temporary patches, create system images for forensics, deploy workarounds
- **Decision**: Contain and clean vs. preserve for forensic analysis (trade-off between business continuity and evidence preservation)
- **Segmentation**: Move unaffected systems to separate VLANs

### 4. Eradication
Remove the root cause and ensure the threat is fully eliminated:
- Remove malware (antivirus, clean installation)
- Patch vulnerabilities that were exploited
- Delete attacker-created accounts, scheduled tasks, services
- Revoke compromised credentials
- Restore clean system images
- Verify complete removal through scanning and monitoring

### 5. Recovery
Safely return affected systems to production:
- Restore systems from clean backups
- Reconnect systems to the network gradually
- Monitor thoroughly for signs of reinfection
- Validate that all security controls are functioning
- Communicate recovery status to stakeholders
- Conduct post-recovery verification

### 6. Lessons Learned (Post-Mortem)
Analyze the incident to improve future response:
- What went well? What went wrong?
- Root cause analysis (RCA)
- Timeline reconstruction
- Update IR plan, playbooks, and procedures
- Implement new controls or modify existing ones
- Conduct training based on gaps identified
- Update threat intelligence sources

## Incident Severity Levels
- **Level 1 (Low)**: Phishing email reported, no data loss. Handled by help desk.
- **Level 2 (Medium)**: Malware infection on a single workstation. IR team lead assigned.
- **Level 3 (High)**: Compromised server with evidence of data exfiltration. Full IR team mobilized.
- **Level 4 (Critical)**: Ransomware affecting multiple systems, APT detection, or PII/PHI breach. Executive leadership, legal, PR, law enforcement involved.

## Key Metrics
- **Dwell Time**: Time from initial compromise to detection. Industry median: ~24 days (Mandiant M-Trends).
- **Mean Time to Detect (MTTD)**: Average time to discover an incident.
- **Mean Time to Respond (MTTR)**: Average time from detection to containment.
- **Mean Time to Recover (MTTR2)**: Average time to restore normal operations.
- **Cost per Incident**: Total financial impact.

## IR Team Roles
- **Incident Manager**: Oversees the response, makes decisions, coordinates resources.
- **Technical Lead**: Directs forensic analysis and technical response.
- **Forensic Analyst**: Collects and analyzes digital evidence.
- **Communications Lead**: Manages internal and external communications.
- **Legal Counsel**: Advises on legal obligations and privilege.
- **HR Representative**: Handles insider threat investigations (employee termination implications).

## Common Interview Questions
1. **What are the phases of the incident response lifecycle?** Preparation → Detection & Analysis → Containment → Eradication → Recovery → Lessons Learned (NIST-based). Or: Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned (SANS).
2. **What is the difference between an IOC and an IOA?** IOC (Indicator of Compromise): Evidence that a system has been breached (hash, IP, domain). IOA (Indicator of Attack): Behavioral pattern indicating an attack in progress (unusual lateral movement, abnormal process execution).
3. **What is the first thing you do when you suspect an incident?** Follow the IR plan. Immediately preserve evidence (capture memory, create forensic images), verify the alert, assess scope, and begin containment to prevent spread.
4. **How do you contain a compromised server?** Disconnect from the network, preserve state (RAM capture, disk image), isolate without powering down (to retain volatile evidence). Apply firewall rules if isolation is needed.
5. **What is dwell time and why does it matter?** Time from compromise to detection. Lower dwell time = less attacker access, less data exfiltration, lower business impact.
6. **How do you handle a ransomware incident?** (1) Isolate systems immediately. (2) Do not pay ransom. (3) Preserve evidence. (4) Contact law enforcement. (5) Determine infection vector. (6) Restore from clean backups. (7) Patch vulnerabilities.

## Further Reading
- [NIST SP 800-61 Rev 2 — Computer Security Incident Handling Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)
- [SANS Incident Response Framework](https://www.sans.org/white-papers/2277/)
- [MITRE ATT&CK (for detection and analysis)](https://attack.mitre.org/)
- [ENISA Incident Handling Guide](https://www.enisa.europa.eu/publications/incident-handling-guide)
- [CISA Incident Response Resources](https://www.cisa.gov/incident-response)
