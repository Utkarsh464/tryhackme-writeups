# Tasks: Become a Defender

## Task 1: SOC Structure
**Purpose:** Understand Security Operations Centre team roles.

**Skills:** Tier 1 (Triage), Tier 2 (Investigation), Tier 3 (Threat Hunting).

**Theory:** SOC analysts are structured in tiers. Tier 1 analysts monitor alerts and triage incidents. Tier 2 analysts conduct deeper investigation and containment. Tier 3 analysts perform advanced threat hunting, forensics, and reverse engineering.

**Commands:** None

---

## Task 2: SIEM and EDR
**Purpose:** Learn about centralised security monitoring tools.

**Skills:** SIEM (Splunk, ELK), EDR (Crowdstrike, SentinelOne).

**Theory:** SIEM (Security Information and Event Management) aggregates logs from multiple sources and generates alerts. EDR (Endpoint Detection and Response) provides visibility into endpoint activity, detecting malicious behaviour at the host level. Together, they form the core of modern SOC monitoring.

**Commands:** None

---

## Task 3: Incident Response Phases
**Purpose:** Understand the structured IR process.

**Skills:** Detection, Analysis, Containment, Eradication, Recovery, Lessons Learned.

**Theory:** The IR process flows from Detection (identifying anomalies) through Analysis (determining scope), Containment (stopping spread), Eradication (removing threat), Recovery (restoring operations), and Lessons Learned (improving future response).

**Commands:** None

---

## Task 4: IoC Analysis
**Purpose:** Analyse indicators of compromise.

**Skills:** IPs, domains, hashes, registry keys.

**Theory:** IoCs are artefacts that indicate a system may be compromised. Common IoCs include suspicious IP addresses, malicious domains, file hashes (MD5, SHA-256), and registry key modifications. IoCs are shared via threat intelligence feeds and used for detection rule creation.

**Commands:** `sha256sum suspicious.exe`

---

## Task 5: Defence in Depth
**Purpose:** Apply layered security controls.

**Skills:** Preventive, detective, corrective, deterrent controls.

**Theory:** Defence in depth uses multiple layers of security so that if one fails, others protect the asset. Preventive controls stop attacks (firewall), detective controls identify them (IDS), corrective controls fix damage (patching), and deterrent controls discourage attackers (warnings).

**Commands:** None

---
