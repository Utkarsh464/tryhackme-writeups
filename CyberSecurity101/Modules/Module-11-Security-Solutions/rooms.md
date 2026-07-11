# Module 11: Security Solutions - Rooms

## Room 1: Introduction to SIEM

- **URL**: https://tryhackme.com/room/introductiontosiem
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

Security Information and Event Management (SIEM) is a cornerstone technology for modern security operations. This room provides a comprehensive introduction to SIEM architecture, data flow, and practical usage. SIEM systems collect log data from diverse sources across the organization (servers, firewalls, endpoints, applications, cloud services), normalize it into a common schema, index it for fast searching, and apply correlation rules to detect security threats in real-time. The room covers the four main components of a SIEM: data collection and forwarding agents, processing and normalization pipeline, storage and indexing engine, and search/visualization/alerting interface. Learners explore popular SIEM platforms including Splunk (with its Search Processing Language SPL), the ELK Stack (Elasticsearch, Logstash, Kibana) as the leading open-source alternative, IBM QRadar, and Microsoft Sentinel. Hands-on exercises include constructing search queries to find specific events, building dashboards to visualize security data, and understanding how correlation rules generate alerts from seemingly unrelated events. The room also covers the role of SIEM in compliance reporting for standards like PCI DSS, HIPAA, and GDPR, where log retention and monitoring are mandatory requirements.

## Room 2: Firewall Fundamentals

- **URL**: https://tryhackme.com/room/firewallfundamentals
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

Firewall Fundamentals covers the evolution, architecture, and configuration of network firewalls. Starting with basic packet filtering firewalls that inspect packet headers (source/destination IP, port, protocol), the room progresses to stateful inspection firewalls that track connection states and only allow traffic that belongs to established connections. Application-layer firewalls and Web Application Firewalls (WAFs) are introduced for filtering traffic based on application content. Next-Generation Firewalls (NGFWs) integrate additional capabilities including intrusion prevention, application identification, SSL inspection, and threat intelligence feeds. Learners practice creating firewall rules with proper source, destination, service, and action definitions. The room covers zone-based security models (inside, outside, DMZ), network address translation (NAT) and port forwarding configurations, and firewall logging best practices. Deployment architectures explored include screened subnet (DMZ), multi-homed firewalls, and cloud firewall services (AWS Security Groups, Azure NSGs). Practical exercises include designing a firewall rule set for a typical organization and analyzing firewall logs to identify allowed and blocked traffic.

## Room 3: IDS Fundamentals

- **URL**: https://tryhackme.com/room/idsfundamentals
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

Intrusion Detection Systems (IDS) and Intrusion Prevention Systems (IPS) monitor network traffic for malicious activity. This room covers the three primary detection methodologies. Signature-based detection matches traffic against known attack patterns (similar to antivirus signatures), offering high accuracy for known threats but inability to detect novel attacks. Anomaly-based detection establishes a baseline of normal network behavior and alerts on significant deviations, capable of detecting unknown attacks but prone to false positives. Stateful protocol analysis understands protocol specifications and flags violations of expected protocol behavior. The room covers Snort and Suricata, the two leading open-source IDS/IPS engines, including rule syntax, alert output formats, and rule management. Learners practice writing and modifying IDS rules, understanding rule options (content matching, PCRE, byte_jump, flow tracking), and tuning rules to reduce false positives. Deployment considerations include inline (IPS) vs passive (IDS) modes, network tap vs SPAN port connectivity, and centralized rule management for distributed sensors. The room also covers how IDS integrates with SIEM for centralized alert correlation and how regular signature updates maintain detection efficacy against emerging threats.

## Room 4: Vulnerability Scanner Overview

- **URL**: https://tryhackme.com/room/vulnerabilityscanneroverview
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

Vulnerability scanners are automated tools that identify security weaknesses in systems, applications, and networks. This room provides a comprehensive overview of the vulnerability scanning lifecycle. Discovery scanning identifies live hosts on the network. Port scanning determines which services are running on each host. Service fingerprinting identifies the specific software and version of each service. Vulnerability detection compares service versions and configurations against a database of known vulnerabilities. Reporting presents findings with severity ratings, descriptions, and remediation recommendations. Remediation tracking monitors the status of vulnerability fixes over time. The room covers popular vulnerability scanners: Nessus (the industry standard commercial scanner with extensive plugin coverage), Qualys (a cloud-based enterprise vulnerability management platform), and OpenVAS (the leading open-source alternative, forked from Nessus). Learners practice configuring scans with appropriate targets, credentials (for credentialed scanning), and scan policies. The room explains the difference between authenticated (credentialed) scans that provide deeper visibility and unauthenticated scans that simulate external attacker perspective. Vulnerability severity is discussed using CVSS (Common Vulnerability Scoring System) scores and their interpretation. The room also covers vulnerability management programs: how organizations prioritize findings (by severity, asset criticality, exploit availability), assign remediation responsibilities (patching, configuration changes, compensating controls), and track progress through dashboards and reports.
