# Module 10: Defensive Security - Rooms

## Room 1: Defensive Security Intro

- **URL**: https://tryhackme.com/room/defensivesecurityintro
- **Difficulty**: Easy
- **Subscription**: Free
- **Estimated Time**: ~30 minutes

This introductory room sets the foundation for defensive security concepts. It explains the fundamental differences between offensive security (red team) and defensive security (blue team), emphasizing that both are essential for comprehensive security programs. The room covers key defensive concepts including defense in depth, the CIA triad (Confidentiality, Integrity, Availability), the principle of least privilege, and security controls (preventive, detective, deterrent, corrective, compensating). Learners are introduced to the security lifecycle: identify assets, protect them, detect threats, respond to incidents, and recover from attacks. This room is designed for complete beginners and requires no prior security experience.

## Room 2: SOC Fundamentals

- **URL**: https://tryhackme.com/room/socfundamentals
- **Difficulty**: Easy
- **Subscription**: Free
- **Estimated Time**: ~1 hour

SOC Fundamentals provides a comprehensive introduction to Security Operations Centers, the teams responsible for monitoring and defending an organization's information systems. The room covers SOC team structures including Tier 1 (triage), Tier 2 (investigation), and Tier 3 (advanced threat hunting) analysts, as well as management and engineering roles. Learners explore SOC tools: SIEM platforms for log aggregation and alerting, EDR for endpoint visibility, SOAR for automated response, and threat intelligence platforms. The room explains SOC processes: alert triage, ticket management, escalation procedures, and shift handovers. Practical exercises involve classifying alerts and making triage decisions.

## Room 3: Digital Forensics Fundamentals

- **URL**: https://tryhackme.com/room/digitalforensicsfundamentals
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

Digital Forensics Fundamentals introduces the science of investigating digital evidence. The room covers forensic principles including Locard's exchange principle (every contact leaves a trace), the importance of maintaining chain of custody, and the order of volatility when collecting evidence. Learners explore forensic acquisition techniques: creating forensic images of disks using tools like dd and FTK Imager, capturing volatile memory with tools like FTK Imager and DumpIt, and collecting network traffic captures. Analysis techniques include file system forensics (understanding file systems, recovering deleted files), Windows registry analysis (identifying persistence mechanisms, USB device history), and timeline creation. The room also discusses legal and ethical considerations in digital forensics.

## Room 4: Incident Response Fundamentals

- **URL**: https://tryhackme.com/room/incidentresponsefundamentals
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

Incident Response Fundamentals teaches the systematic approach to handling cybersecurity incidents. Based on the NIST SP 800-61 framework, the room covers the four-phase incident response lifecycle. The Preparation phase covers creating incident response plans, assembling response teams (CSIRT), and establishing communication channels. The Detection and Analysis phase covers identifying Indicators of Compromise (IoCs), analyzing alerts, and determining incident scope and severity. The Containment, Eradication, and Recovery phase covers isolating affected systems, removing threats, restoring systems from clean backups, and monitoring for recurrence. The Post-Incident Activity phase covers lessons learned, documentation, and improving security posture. Learners practice triaging incidents and making containment decisions.

## Room 5: Logs Fundamentals

- **URL**: https://tryhackme.com/room/logsfundamentals
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

Logs Fundamentals covers the essential skill of log analysis for security monitoring and incident investigation. The room explores different types of logs: Windows Event Logs (Application, System, Security), Linux system logs (/var/log/), web server access logs (Apache, Nginx), firewall logs, authentication logs, and application logs. Learners practice reading and interpreting log entries, understanding timestamps, event IDs, and log levels. The room covers log collection with Syslog and Windows Event Forwarding, log parsing and normalization, and using tools like grep, awk, and Logstash for log analysis. Practical exercises involve identifying suspicious activities from log data, including brute-force attacks, privilege escalation, and data exfiltration attempts.
