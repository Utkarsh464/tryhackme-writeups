# IDS Fundamentals

## Room Information
- **URL**: https://tryhackme.com/room/idsfundamentals
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

## Description

IDS Fundamentals covers Intrusion Detection Systems (IDS) and Intrusion Prevention Systems (IPS), technologies that monitor network traffic for malicious activity and either alert on it (IDS) or block it (IPS). These systems are critical components of a defense-in-depth strategy, providing visibility into network-level threats that may bypass other security controls. This room explores the three primary detection methodologies used by IDS/IPS systems. Signature-based detection compares network traffic against a database of known attack patterns (signatures), similar to how antivirus software identifies malware. Signatures can match specific byte sequences, packet headers, or combinations of conditions. Signature matching is fast and accurate for known threats but cannot detect novel or variant attacks. Anomaly-based detection establishes a baseline of normal network behavior using machine learning or statistical analysis and alerts on significant deviations. This approach can detect previously unknown attacks (zero-days) but tends to generate more false positives. Stateful protocol analysis understands the specifications of network protocols (HTTP, FTP, SMB, DNS) and flags violations of expected protocol behavior, such as malformed packets, invalid command sequences, or out-of-bounds values. The room focuses on Snort and Suricata, the two leading open-source IDS/IPS engines. Snort, developed by Cisco, is the most widely deployed IDS/IPS with a large community and extensive rule sets. Suricata, developed by the Open Information Security Foundation (OISF), offers multi-threaded processing for better performance on modern hardware and supports GPU acceleration, file extraction, and Lua scripting for custom detection logic. Learners practice writing and modifying IDS rules, understanding Snort/Suricata rule syntax including rule headers (action, protocol, source/destination, port) and rule options (content matching, PCRE regular expressions, flow tracking, byte_test, and metadata). Deployment considerations include inline (IPS) mode where traffic passes through the device and malicious packets are dropped, vs passive (IDS) mode where traffic is monitored via a SPAN port or network tap. The room also covers rule management, tuning to reduce false positives, and integration with SIEM platforms for centralized alert correlation.

## Objectives
- Understand IDS and IPS technologies and their differences
- Differentiate signature-based, anomaly-based, and protocol analysis detection
- Write and modify Snort/Suricata detection rules
- Deploy IDS in passive mode and IPS in inline mode
- Tune IDS rules to reduce false positives
- Integrate IDS alerts with SIEM platforms

## Tools
- Snort
- Suricata
- PulledPork (rule management for Snort)
- Wireshark (for traffic analysis and rule testing)

## Concepts
- Network-based IDS (NIDS) vs Host-based IDS (HIDS)
- Signature-based detection
- Anomaly-based detection
- Stateful protocol analysis
- Inline (IPS) vs Passive (IDS) deployment
- Rule structure and syntax (Snort/Suricata rule language)
- False positives and rule tuning
- Alert output formats (syslog, unified2, JSON)
