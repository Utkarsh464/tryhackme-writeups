# IDS Fundamentals - Tasks

## Task 1: Introduction to IDS/IPS
- Understand the purpose of intrusion detection and prevention
- Differentiate between NIDS and HIDS
- Understand IDS vs IPS: detect vs prevent
- Learn about the evolution of IDS technology

## Task 2: Detection Methodologies
- Understand signature-based detection and its strengths/weaknesses
- Understand anomaly-based detection and its strengths/weaknesses
- Understand stateful protocol analysis
- Compare detection methodologies for different threat types

## Task 3: Snort/Suricata Rule Structure
- Learn the rule header: action, protocol, source/destination IP, source/destination port, direction
- Learn the rule body (options): content, offset, depth, pcre, flow, sid, rev, reference, classtype, msg
- Understand rule ordering and priority
- Write basic detection rules for common attacks

## Task 4: Content Matching in Rules
- Use `content` for matching specific byte sequences
- Use `offset` and `depth` to limit search scope
- Use `distance` and `within` for relative positioning
- Use `pcre` for Perl-compatible regular expressions
- Combine multiple content matches with logical conditions

## Task 5: Flow and State Tracking
- Use `flow` keywords for connection state (to_server, from_server, established)
- Use `flowbits` for state tracking across multiple rules
- Create rules that detect multi-step attacks
- Understand stream reassembly and its importance

## Task 6: Rule Management and Categories
- Understand rule categories and classtypes
- Configure rule files and include paths
- Use PulledPork or Oinkmaster for rule updates
- Enable and disable specific rules
- Create local custom rules

## Task 7: Deploying Snort/Suricata
- Install Snort or Suricata on Linux
- Configure network interfaces for monitoring
- Set up as passive IDS (via SPAN port or tap)
- Set up as inline IPS
- Verify traffic is being processed

## Task 8: Alert Output and Logging
- Configure alert output formats (fast, full, unified2, JSON)
- Send alerts to syslog for SIEM integration
- Configure log rotation and retention
- Analyze alert output for investigations
- Use barnyard2 for efficient alert processing

## Task 9: Tuning and False Positive Reduction
- Identify common sources of false positives
- Use threshold configurations to suppress noisy rules
- Modify rules to reduce false positives without losing detection
- Create suppression lists for known legitimate traffic
- Use pass rules to explicitly whitelist traffic

## Task 10: Performance Considerations
- Understand the impact of rule complexity on performance
- Configure preprocessors for optimal performance
- Suricata multi-threading and AF_PACKET vs NFQueue
- Monitor IDS performance metrics
- Scale IDS deployment for high-bandwidth networks

## Task 11: Practical IDS Exercise
- Install and configure Snort or Suricata
- Write custom rules to detect specific attacks
- Generate test traffic and verify detection
- Analyze alert output and tune rules
- Integrate alerts with a SIEM dashboard
