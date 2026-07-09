# Threat Intelligence

## Definition
Threat intelligence (TI) is evidence-based knowledge about existing or emerging threats to an organization, including context, mechanisms, indicators, implications, and actionable advice. It transforms raw data (logs, alerts, samples) into meaningful information that enables organizations to make informed security decisions. TI is categorized into strategic (high-level, executive), operational (campaigns, TTPs), tactical (IOCs, signatures), and technical (specific indicators for automated defense).

## Why It Matters
Organizations face thousands of threats daily. Without threat intelligence, security teams are reactive — always catching up to attacks that have already happened. TI enables proactive defense: blocking known malicious infrastructure before it's used, prioritizing patching based on actively exploited vulnerabilities, understanding attacker motivations and capabilities, and making informed risk management decisions. TI transforms security from a cost center to a strategic capability.

## Where It Appears in the Path
Threat intelligence is an advanced topic typically covered in the defensive security module. It builds on incident response, SIEM, malware analysis, and networking. TI feeds into SIEM correlation, firewall rules, endpoint detection, vulnerability prioritization, and executive reporting.

## Prerequisites
- Understanding of cyber attacks and malware
- Incident response knowledge
- SIEM/log analysis basics
- Networking fundamentals (IPs, domains, protocols)

## Key Concepts

### Indicators of Compromise (IOCs)
Artifacts that indicate a system has been compromised. IOCs are the "what" — the technical evidence of an intrusion.
- **Network IOCs**: IP addresses, domain names, URLs, user-agent strings, SSL/TLS certificate fingerprints
- **Host IOCs**: File hashes (MD5, SHA-1, SHA-256), file paths, registry keys, mutex names, process names, service names
- **Behavioral IOCs**: Unusual account behavior, anomalous network traffic patterns, unexpected process creation

### TTPs (Tactics, Techniques, and Procedures)
The "how" of an attack — describing the methods and behaviors of threat actors.
- **Tactics**: The "why" — the goal of a step (MITRE ATT&CK: Initial Access, Execution, Persistence, Defense Evasion, etc.)
- **Techniques**: The "how" — the method to achieve the goal (T1078: Valid Accounts, T1059: Command and Scripting Interpreter)
- **Procedures**: The specific implementation — the detailed steps a particular APT group takes

MITRE ATT&CK is the industry-standard framework for documenting TTPs.

### Threat Actors
- **APT (Advanced Persistent Threat)**: Nation-state sponsored, highly skilled, long-term campaigns. Examples: APT28 (Fancy Bear), APT29 (Cozy Bear), Lazarus Group (North Korea).
- **Cybercriminal Groups**: Financially motivated (ransomware, data theft). Examples: Conti, FIN7, LockBit, TrickBot.
- **Hacktivists**: Ideologically motivated (defacement, DDoS). Examples: Anonymous, Killnet.
- **Insider Threats**: Current/former employees, contractors. Motivations: financial, revenge, ideology.
- **Script Kiddies**: Low-skill attackers using existing tools.

### Intelligence Sources

**Open Source Intelligence (OSINT)**:
- Public threat feeds: AlienVault OTX, VirusTotal, IBM X-Force, Spamhaus
- Dark web forums and marketplaces
- Social media, Telegram, Discord channels
- Shodan, Censys (Internet scanning)
- MITRE ATT&CK, CAPEC, CWE
- National CERTs (CISA, NCSC, ENISA)

**Commercial Intelligence**:
- Recorded Future, Mandiant Threat Intelligence, CrowdStrike Falcon, Intel471
- Industry-specific ISACs (Information Sharing and Analysis Centers): FS-ISAC (finance), IT-ISAC, REN-ISAC (education)
- MISP (Malware Information Sharing Platform) — community-driven sharing

**Internal Intelligence**:
- Historical incident data and post-mortems
- SIEM/EDR telemetry
- Honeypot data
- Phishing reports from users
- Vulnerability scan data

## Intelligence Lifecycle
The process of converting raw data into actionable intelligence:

1. **Direction**: Define intelligence requirements. What decisions need to be supported? What threats are most relevant to the organization? Priority Intelligence Requirements (PIRs) guide collection.

2. **Collection**: Gather raw data from all relevant sources (OSINT, commercial feeds, internal logs, industry sharing groups, dark web monitoring).

3. **Processing**: Convert raw data into usable formats. Normalize, deduplicate, enrich with context. Extract IOCs, correlate with existing data, format for automated consumption (STIX/TAXII, MISP, JSON).

4. **Analysis**: Transform processed data into intelligence. Identify patterns, attribute activity to known actors, assess relevance and confidence, produce judgments. This is where raw data becomes actionable.

5. **Dissemination**: Deliver intelligence to the right consumers in the right format. Tactical (automated feeds to SIEM/firewalls), operational (analyst briefings), strategic (executive summaries, risk assessments).

6. **Feedback**: Collect feedback from consumers to improve future intelligence. Are the intelligence products useful? What new requirements emerged? What was missed?

## Threat Intelligence Platforms (TIPs)
Software that aggregates, correlates, and analyzes threat data from multiple sources.
- **MISP**: Open-source threat intelligence platform. Community-driven IOC sharing.
- **ThreatConnect**: Commercial TIP with orchestration and automation.
- **Anomali**: Threat intelligence platform with extensive integrations.
- **Palo Alto Cortex XSOAR**: SOAR platform with built-in TI capabilities.

## Intelligence Sharing Standards
- **STIX (Structured Threat Information Expression)**: Standardized language for describing threat intelligence. Objects: Indicator, Campaign, Threat Actor, Attack Pattern, Course of Action, Report.
- **TAXII (Trusted Automated Exchange of Indicator Information)**: Protocol for exchanging STIX data over HTTPS.
- **OpenIOC**: Mandiant's XML-based IOC format.
- **CyBOX (Cyber Observable Expression)**: Standard for describing system/network observations (part of STIX).

## Common Interview Questions
1. **What is threat intelligence and why is it important?** Evidence-based knowledge about threats that enables proactive defense. Transforms security from reactive to proactive by providing context about attacker TTPs, IOCs, and motivations.
2. **What is the difference between tactical and strategic threat intelligence?** Tactical: IOCs, signatures, immediate blocking (for SOC, network defenders). Strategic: threat landscape, risk trends, business impact (for CISOs, executives).
3. **What is MITRE ATT&CK and how is it used?** Knowledge base of adversary TTPs organized by tactics and techniques. Used for threat modeling, gap analysis, detection engineering, and intelligence reporting.
4. **What is the intelligence lifecycle?** Direction → Collection → Processing → Analysis → Dissemination → Feedback. Converts raw data into actionable intelligence.
5. **What is the difference between an IOC and a TTP?** IOC: indicator (IP, hash, domain) — what to look for. TTP: method (how they attack) — behavior and patterns. TTPs are more durable and harder for attackers to change.
6. **How do you measure the effectiveness of threat intelligence?** Relevance (do IOCs/TTPs match your environment?), Timeliness (how fast are IOCs available?), Actionability (can you automate responses?), Accuracy (false positive rate), Coverage (what threats are you missing?).

## Further Reading
- [MITRE ATT&CK](https://attack.mitre.org/)
- [CISA Threat Intelligence](https://www.cisa.gov/topics/cyber-threats-advisories)
- [MISP Project](https://www.misp-project.org/)
- [STIX/TAXII](https://oasis-open.github.io/cti-documentation/)
- _Intelligence-Driven Incident Response_ by Scott Roberts and Rebekah Brown
- [SANS CTI Summit Papers](https://www.sans.org/cyber-security-summit/archives/file/cti-summit)
- TryHackMe: Threat Intelligence room
