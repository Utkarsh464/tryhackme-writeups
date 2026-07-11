# Incident Response Fundamentals - Tasks

## Task 1: Introduction to Incident Response
- Understand what constitutes a security incident
- Differentiate between events, alerts, and incidents
- Understand why structured incident response is essential
- Learn about the NIST SP 800-61 framework

## Task 2: Preparation Phase
- Develop an incident response plan and policy
- Assemble a Computer Security Incident Response Team (CSIRT)
- Identify roles and responsibilities within the team
- Acquire necessary tools (forensic kits, communication tools, analysis tools)
- Conduct training, tabletop exercises, and simulations
- Establish communication channels and escalation paths

## Task 3: Detection and Analysis - Alert Sources
- Understand SIEM alerts and correlation rules
- Interpret EDR detections and endpoint alerts
- Handle user-reported suspicious activity
- Incorporate threat intelligence feeds
- Understand network-based detection (IDS/IPS, firewall logs)

## Task 4: Detection and Analysis - Indicators of Compromise
- Define and identify atomic IoCs (IPs, domains, email addresses, URLs)
- Define and identify computed IoCs (file hashes: MD5, SHA-1, SHA-256)
- Define and identify behavioral IoCs (unusual login patterns, data transfer anomalies)
- Correlate multiple IoCs to confirm incidents
- Understand TTPs (Tactics, Techniques, Procedures) vs IoCs

## Task 5: Incident Triage and Classification
- Classify incidents by type (malware, phishing, unauthorized access, data breach, DoS)
- Prioritize incidents by severity (critical, high, medium, low)
- Determine incident scope (affected systems, users, data)
- Escalate incidents according to severity and procedures
- Document initial findings and create incident tickets

## Task 6: Containment Phase
- Understand short-term containment strategies (isolate host, disable account, block IP)
- Understand long-term containment strategies (apply temporary patches, implement firewall rules)
- Make containment decisions based on incident type and impact
- Balance containment speed with evidence preservation
- Implement containment without alerting attackers

## Task 7: Eradication Phase
- Remove malware from affected systems
- Close attacker backdoors and remove persistence mechanisms
- Patch vulnerabilities that were exploited
- Reset compromised credentials
- Verify eradication through scanning and monitoring

## Task 8: Recovery Phase
- Restore systems from clean backups
- Implement additional security controls
- Monitor for signs of attacker return
- Gradually return systems to production
- Verify system integrity after restoration

## Task 9: Post-Incident Activity
- Conduct lessons learned meetings with all stakeholders
- Document the complete incident timeline and actions taken
- Update incident response plans and procedures
- Implement security improvements based on findings
- Determine evidence retention requirements

## Task 10: Communication and Legal Considerations
- Understand when to notify management and executives
- Know when to involve legal counsel and law enforcement
- Understand data breach notification laws and timelines
- Communicate with affected customers and partners
- Handle media inquiries and public relations

## Task 11: Practical Incident Response Exercise
- Receive and triage a simulated security alert
- Investigate the incident using available tools
- Make containment and eradication decisions
- Document findings and prepare an incident report
- Conduct a lessons learned review
