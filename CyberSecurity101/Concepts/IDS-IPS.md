# IDS / IPS

## Definition
Intrusion Detection Systems (IDS) and Intrusion Prevention Systems (IPS) are network security technologies that monitor network traffic and system activity for malicious behavior or policy violations. IDS detects and alerts on suspicious activity (passive, out-of-band). IPS detects and actively blocks or prevents malicious traffic in real time (inline). Both use signature-based detection, anomaly-based detection, or a combination.

## Why It Matters
IDS/IPS provides critical visibility and protection against network attacks that firewalls cannot block. Firewalls control access (who can connect where), but IDS/IPS identifies what is happening within allowed traffic — malicious payloads, exploit attempts, malware communication, policy violations. In the modern threat landscape, IDS/IPS is essential for detecting advanced threats, zero-day exploits, and insider threats.

## Where It Appears in the Path
IDS/IPS is covered in the network security module alongside firewalls. It integrates with SIEM (IDS alerts feed into SIEM), incident response (IDS provides detection evidence), and penetration testing (evading IDS is a skill). Common platforms: Snort, Suricata, Zeek (formerly Bro).

## Prerequisites
- Networking fundamentals (TCP/IP, ports, protocols)
- Firewall concepts
- Basic understanding of attacks (port scans, DoS, exploits)

## Detection Methods

### Signature-Based Detection
Compares traffic against a database of known attack patterns (signatures). Similar to antivirus — effective for known threats, fails against zero-days and variants. Requires regular signature updates. Low false positive rate for well-tuned signatures.
- **Example**: Signature for EternalBlue: look for SMB Trans2 request with specific buffer size.

### Anomaly-Based Detection
Establishes a baseline of "normal" network behavior (traffic volumes, protocol distributions, port usage patterns) and alerts on deviations. Can detect novel attacks and zero-days. Higher false positive rate. Requires careful tuning to avoid alert fatigue.

### Stateful Protocol Analysis
Compares traffic against protocol specifications to detect violations. Detects malformed packets, command injections, protocol tunneling. Examples: HTTP requests with overly long headers, DNS responses larger than queries, SMTP commands in non-standard order.

### Behavioral Analysis
Tracks entity behavior over time (similar to UEBA in SIEM). Identifies slow and low attacks, insider threats, and compromised accounts. Example: a finance user suddenly accessing HR databases at 3 AM.

## IDS vs IPS

| Feature | IDS | IPS |
|---------|-----|-----|
| Placement | Out-of-band (monitors mirrored traffic) | Inline (traffic flows through it) |
| Action | Alert only | Alert and block/drop traffic |
| Latency Impact | None | Adds latency (processing in path) |
| Risk | No impact on legitimate traffic | Risk of dropping legitimate traffic (false positive) |
| Common Use | Monitoring, forensics | Active prevention |

## Network-Based vs Host-Based

### NIDS (Network-based IDS)
Monitors network traffic passing through a network segment. Typically placed at network chokepoints (behind firewall, in DMZ, on backbone). Analyzes packet headers and payloads.
- Pros: No software on endpoints, monitors all traffic
- Cons: Cannot inspect encrypted traffic without decryption, can be overwhelmed by traffic volume

### HIDS (Host-based IDS)
Installed on individual hosts (servers, endpoints). Monitors system logs, file integrity, process activity, registry changes, and network connections on that host.
- Pros: Can analyze encrypted traffic (after decryption on host), detects local attacks (privilege escalation, malware), file integrity monitoring
- Cons: Must be installed on each host, consumes system resources
- Examples: OSSEC, Wazuh, Tripwire, AIDE

## Key IDS/IPS Platforms

### Snort
Open-source NIDS/NIPS by Cisco. Rule-based signature detection. Lightweight, widely used. Rule format:
```
alert tcp $EXTERNAL_NET any -> $HOME_NET 80 (msg:"SQL Injection Attempt"; content:"UNION SELECT"; sid:1000001; rev:1;)
```

### Suricata
Open-source NIDS/NIPS/NGFW engine. Multi-threaded (better performance than Snort). Supports file extraction, TLS fingerprinting, HTTP logging, protocol parsing, and Lua scripting. Uses same rule format as Snort (Emerging Threats rules).

### Zeek (formerly Bro)
Open-source network analysis framework. Not a traditional signature-based IDS — focuses on deep protocol analysis, logging, and scripting for detection. Excellent for network forensics. Produces detailed logs (conn.log, http.log, dns.log, ssl.log, files.log).

### OSSEC / Wazuh
Open-source HIDS. File integrity monitoring, log analysis, rootkit detection, active response. Wazuh is the modern fork with SIEM capabilities.

## Rule Management
- **Emerging Threats (ET)**: Free and paid rule sets for Snort/Suricata
- **Sourcefire VRT**: Talos (Cisco) rule set
- **Custom Rules**: Organizations write specific rules for their environment
- **False Positive Tuning**: Suppress known good behavior, adjust thresholds, whitelist trusted sources

## Evasion Techniques
- **Fragmentation**: Split malicious payload across multiple packets
- **Encoding**: URL encoding, base64, UTF-8 encoding
- **Encryption**: TLS/SSL hides payload from NIDS
- **Obfuscation**: NOP sleds, polymorphic shellcode
- **Split HTTP requests**: Use chunked encoding or multiple headers
- **Timing attacks**: Slow data exfiltration to appear normal
- **IP defragmentation issues**: Send fragments that reassemble differently on target vs IDS

## Common Interview Questions
1. **What is the difference between IDS and IPS?** IDS monitors and alerts (passive, out-of-band). IPS sits inline and actively blocks malicious traffic.
2. **What is the difference between signature-based and anomaly-based detection?** Signature-based matches known attack patterns (low false positives, misses new attacks). Anomaly-based flags deviations from baseline (catches new attacks, higher false positives).
3. **What is the difference between NIDS and HIDS?** NIDS monitors network traffic (all hosts on segment). HIDS monitors activity on individual hosts (file integrity, logs, processes).
4. **How can an attacker evade IDS?** Fragmentation, encryption, encoding (URL/base64), obfuscation, timing attacks, splitting payloads across packets.
5. **What is the role of IDS/IPS in a defense-in-depth strategy?** IDS/IPS provides detection and prevention layer between the firewall and the endpoint. Firewall allows/denies ports — IDS inspects what's inside allowed traffic.
6. **How do you tune an IDS to reduce false positives?** (1) Whitelist known good traffic. (2) Adjust rule thresholds. (3) Disable irrelevant rules. (4) Modify rule content to match environment. (5) Use asset criticality in alert scoring.

## Further Reading
- [Snort User Manual](https://www.snort.org/documents)
- [Suricata Documentation](https://suricata.readthedocs.io/)
- [Zeek User Manual](https://docs.zeek.org/en/current/)
- [Emerging Threats Rules](https://rules.emergingthreats.net/)
- [NIST SP 800-94 Rev 1 — Intrusion Detection and Prevention Systems](https://csrc.nist.gov/publications/detail/sp/800-94/rev-1/final)
- TryHackMe: "Snort" and "Zeek" rooms
