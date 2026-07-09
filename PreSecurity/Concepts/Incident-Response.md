# Incident Response

## Definition
Incident Response (IR) is a structured approach to handling security incidents. The core phases are: **Preparation** (tools, playbooks, training), **Detection & Analysis** (SIEM alerts, log review), **Containment, Eradication & Recovery** (stop spread, remove threat, restore systems), and **Post-Incident Activity** (lessons learned, report). A **SOC** (Security Operations Center) monitors for threats using **SIEM** (Security Information and Event Management) and **EDR** (Endpoint Detection and Response) tools.

## Why It Matters
IR minimizes damage, reduces recovery time, and preserves evidence for legal action. Without a proper IR process, breaches escalate, data is lost, and compliance is violated. SIEM correlation and EDR telemetry are the primary detection mechanisms in modern SOCs.

## Where It Appears in the Path
- Security Operations
- Incident Response modules

## Prerequisites
- Networking, OS fundamentals, basic security concepts

## Key Points
- NIST SP 800-61 defines the IR lifecycle
- SOC tiers: T1 (triage), T2 (investigate), T3 (hunt/threat intel)
- SIEM: log aggregation, correlation rules, alerting
- EDR: endpoint telemetry, behavior analysis, remote containment

## Common Interview Questions
1. What is the difference between a SIEM and EDR?
**Answer:** SIEM aggregates and correlates logs from multiple sources; EDR monitors endpoint behavior specifically.
2. What is the first step in incident response?
**Answer:** Preparation — having tools, access, and playbooks ready before an incident.
3. What is the purpose of a post-mortem?
**Answer:** Identify root cause, improve processes, prevent recurrence.

## Further Reading
- NIST SP 800-61 Rev 2
- SANS Incident Response Poster
- MITRE ATT&CK Framework