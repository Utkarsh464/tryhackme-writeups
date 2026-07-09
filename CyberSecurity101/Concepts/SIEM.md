# SIEM

## Definition
Security Information and Event Management (SIEM) is a centralized solution that aggregates log data from across an organization's IT infrastructure, normalizes and correlates the data, generates alerts for suspicious activity, and provides dashboards for security monitoring. SIEM combines SIM (Security Information Management — long-term storage, analysis, reporting) and SEM (Security Event Management — real-time monitoring, correlation, alerting).

## Why It Matters
Modern enterprises generate millions of logs daily from servers, endpoints, firewalls, applications, cloud services, and network devices. Manually reviewing this data is impossible. SIEM systems automate log collection, correlation, and alerting, enabling security teams to detect threats in real time, investigate incidents with full context, and meet compliance requirements (PCI DSS, HIPAA, SOX, GDPR) that mandate log retention and review.

## Where It Appears in the Path
SIEM is a core defensive/blue team topic. It builds on networking fundamentals (log sources), Windows/Linux logging, threat intelligence (IOC ingestion), and incident response (IR uses SIEM data). Practical exercises often use Splunk, ELK Stack (Elasticsearch, Logstash, Kibana), or Wazuh.

## Prerequisites
- Basic understanding of logs (syslog, Windows Event Log, application logs)
- Networking fundamentals
- Incident response knowledge helpful

## Core SIEM Processes

### Log Collection
Logs are collected from various sources:
- **Log Shippers**: Agents (Winlogbeat, Filebeat, Sysmon, Splunk Universal Forwarder) installed on endpoints that forward logs to the SIEM.
- **Syslog**: Standard protocol for log forwarding (UDP 514, TCP 514, or TCP 6514 for TLS syslog).
- **API Integration**: Cloud services (AWS CloudTrail, Azure Sentinel, Office 365) and SaaS platforms.
- **Database/Agentless**: Pull logs via WMI, SSH, or database queries.

Common log sources: Windows Event Logs, Sysmon, Linux auth.log/syslog, firewall logs, web server logs (Apache/Nginx/IIS), DNS logs, DHCP logs, antivirus/EDR logs, VPN logs, cloud audit logs.

### Normalization
Logs from different sources have different formats. SIEMs parse and normalize them into a common schema. Fields like timestamp, source IP, destination IP, username, event type, severity are extracted and standardized. Examples: Common Event Format (CEF), Log Event Extended Format (LEEF), Elastic Common Schema (ECS).

### Correlation
The heart of SIEM — analyzing event relationships to identify threats. Correlation rules define conditions that indicate malicious activity:
```
RULE: Multiple failed logins followed by successful login
WHEN: Count(failed_login) > 5 from same source IP within 5 minutes
       AND successful_login within 2 minutes
THEN: ALERT "Brute-force attack detected"
```

### Alerting
When correlation rules trigger, the SIEM generates alerts. Alerts have severity levels (low, medium, high, critical), assigned to analysts, and typically include:
- Alert name and description
- Timestamp and time range
- Affected systems and users
- Raw log entries
- Recommended actions
- MITRE ATT&CK mapping (most modern SIEMs support this)

### Dashboards and Reporting
Visual displays of security data: real-time dashboards (current events), historical dashboards (trends, anomalies), compliance reports (PCI DSS log review, failed login reports), executive summaries.

## Key SIEM Capabilities

### Threat Intelligence Integration
Ingest feeds of known malicious IOCs (IPs, domains, hashes) and cross-reference against log data. Automated alerting when a known bad IOC appears in the environment.

### User and Entity Behavior Analytics (UEBA)
Machine learning models establish baselines of normal user/device behavior. Anomalies (unusual login times, data access patterns, lateral movement) generate alerts. Detects insider threats and compromised accounts.

### Case Management
Track investigations within the SIEM: assign alerts to analysts, add notes, attach evidence, link related alerts, document remediation actions, and close cases with findings.

### Retention & Archiving
Compliance requirements mandate log retention periods (e.g., PCI DSS: 1 year, with 3 months immediately accessible). SIEMs manage storage tiers (hot/warm/cold/archive) to balance access speed and cost.

## Popular SIEM Solutions

### Splunk
Market leader. Powerful search language (SPL), extensive app ecosystem, machine learning toolkit. Can be expensive. Used by large enterprises.

### ELK Stack (Elastic)
Open-source foundation: Elasticsearch (storage and search), Logstash (log processing), Kibana (visualization). Elastic Security adds SIEM features. Flexible but requires more engineering effort.

### Microsoft Sentinel
Cloud-native SIEM on Azure. Integrates deeply with Microsoft 365 and Azure services. Built-in UEBA and threat intelligence. Pay-as-you-go pricing.

### IBM QRadar
On-premises and cloud. Strong correlation engine, offense-based alerting (groups related events). Widely used in finance and government.

### Wazuh
Open-source SIEM and XDR. Forked from OSSEC. Integrates with ELK. Good for budget-constrained organizations.

## Common Detection Use Cases
- **Brute-force attacks**: Multiple failed logins
- **Lateral movement**: Pass-the-hash detections, unusual RDP/PSExec connections
- **Malware infection**: Beaconing (C2 communications), suspicious process creation, registry persistence
- **Data exfiltration**: Large outbound data transfers, unusual DNS queries (DNS tunneling)
- **Privilege escalation**: Unusual account creation, group membership changes
- **Insider threat**: Accessing files outside normal hours or from unusual locations
- **Ransomware**: Mass file extension changes, high file modification rates, volume shadow copy deletion

## Common Interview Questions
1. **What is SIEM and what are its core components?** Security Information and Event Management. Components: log collection, normalization, correlation engine, alerting, dashboards, reporting, case management.
2. **What is the difference between SIEM and log management?** Log management stores and indexes logs for search. SIEM adds correlation, alerting, and security-specific analysis. SIEM is a superset of log management.
3. **How do you create a correlation rule for brute force detection?** Count failed login events from same source IP exceeding threshold within time window, optionally chained with successful login.
4. **What is the difference between false positive and false negative in SIEM?** False positive: benign event flagged as malicious (wastes analyst time). False negative: malicious event not flagged (worse — attack goes undetected).
5. **What metrics are important for SIEM operations?** Mean Time to Detect (MTTD), Mean Time to Respond (MTTR), alerts per day, false positive rate, actionable alert percentage, average investigation time.
6. **How do you tune a SIEM to reduce false positives?** (1) Whitelist known safe activity. (2) Adjust thresholds. (3) Combine multiple low-confidence indicators. (4) Use asset criticality weighting. (5) Feed threat intelligence. (6) Regularly review and update rules.

## Further Reading
- [SANS SIEM Cheat Sheet](https://www.sans.org/white-papers/33434/)
- [ELK Stack Tutorial](https://www.elastic.co/guide/index.html)
- [Splunk Tutorial (Splunk Fundamentals)](https://www.splunk.com/en_us/training.html)
- [MITRE ATT&CK for SIEM correlation](https://attack.mitre.org/)
- [SIEM Buyer's Guide (Gartner)](https://www.gartner.com/en/documents/3984992)
- TryHackMe: "Splunk 101" and "Wazuh" rooms
