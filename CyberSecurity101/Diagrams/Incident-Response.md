# NIST Incident Response Lifecycle — Preparation Through Lessons Learned

```mermaid
graph TB
    subgraph Prep["1. Preparation"]
        P1["Develop IR policy & procedures"]
        P2["Create Incident Response Team (CSIRT)"]
        P3["Deploy detection tools: SIEM, EDR, IDS/IPS"]
        P4["Conduct tabletop exercises & drills"]
        P5["Build playbooks for common scenarios"]
    end

    subgraph Detect["2. Detection & Analysis"]
        D1["Alert triggers: SIEM rule, AV alert, user report"]
        D2["Triage: is this a real incident?"]
        D3["Scope: affected systems, users, data"]
        D4["Collect evidence: memory dump, disk image, logs"]
        D5["Determine severity: low / medium / high / critical"]
    end

    subgraph Contain["3. Containment, Eradication & Recovery"]
        subgraph ShortTerm["Short-Term Containment"]
            C1["Isolate affected hosts from network"]
            C2["Block malicious IPs on firewall"]
            C3["Disable compromised accounts"]
        end

        subgraph LongTerm["Long-Term Eradication"]
            C4["Remove malware from systems"]
            C5["Patch exploited vulnerabilities"]
            C6["Reset passwords & rotate credentials"]
        end

        subgraph Recovery["Recovery"]
            C7["Restore from clean backups"]
            C8["Monitor for reinfection"]
            C9["Gradually return systems to production"]
        end
    end

    subgraph Lessons["4. Lessons Learned"]
        L1["Post-incident review meeting (within 2 weeks)"]
        L2["Create incident report: timeline, root cause, impact"]
        L3["Update playbooks & detection rules"]
        L4["Implement new controls to prevent recurrence"]
        L5["Share intelligence: IoCs, TTPs with community"]
    end

    Prep --> Detect --> Contain --> Lessons
    Lessons -.->|Feed back| Prep

    style Prep fill:#1a5276,color:#fff
    style Detect fill:#e67e22,color:#fff
    style Contain fill:#c0392b,color:#fff
    style Lessons fill:#27ae60,color:#fff
```

The NIST SP 800-61 Incident Response Lifecycle provides a structured framework for handling security incidents effectively. **Phase 1 — Preparation**: This is the most critical phase. The organization must have a written IR policy, a trained Computer Security Incident Response Team (CSIRT), deployed detection tools (SIEM, EDR, IDS/IPS), and tested playbooks. Preparation also includes hardening systems, backup strategies, and user awareness training. Without preparation, incident response becomes chaotic and ineffective. **Phase 2 — Detection & Analysis**: Incidents are detected through automated alerts or manual reports. The IR team triages alerts to distinguish true incidents from false positives, determines the scope (what systems, users, and data are affected), and collects forensic evidence (memory captures, disk images, network logs) while preserving chain of custody. Severity is assigned based on data sensitivity, business impact, and regulatory obligations. **Phase 3 — Containment, Eradication & Recovery**: Short-term containment stops the bleeding — isolating hosts, blocking IPs, and disabling accounts. Long-term eradication removes the root cause — deleting malware, patching vulnerabilities, and rotating credentials. Recovery involves restoring systems from clean backups and monitoring for signs of reinfection before returning to production. **Phase 4 — Lessons Learned**: Within two weeks of closure, the team conducts a post-incident review to document what happened, what worked, and what failed. The output feeds back into the Preparation phase, creating a continuous improvement loop. Sharing indicators of compromise (IoCs) with industry peers strengthens collective defense.
