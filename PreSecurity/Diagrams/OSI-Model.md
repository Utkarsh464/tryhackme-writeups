# OSI Model

```mermaid
graph TD
    L7[7 - Application] --> L6[6 - Presentation]
    L6 --> L5[5 - Session]
    L5 --> L4[4 - Transport]
    L4 --> L3[3 - Network]
    L3 --> L2[2 - Data Link]
    L2 --> L1[1 - Physical]

    L7 -->|HTTP, FTP, DNS, SMTP| P7[HTTP, FTP, DNS, SMTP]
    L6 -->|TLS, SSL, JPEG, ASCII| P6[TLS, SSL, JPEG, ASCII]
    L5 -->|NetBIOS, RPC, PPTP| P5[NetBIOS, RPC, PPTP]
    L4 -->|TCP, UDP| P4[TCP, UDP]
    L3 -->|IP, ICMP, ARP, OSPF| P3[IP, ICMP, ARP, OSPF]
    L2 -->|Ethernet, PPP, Switch| P2[Ethernet, PPP, Switch]
    L1 -->|RJ45, Fiber, Hubs, Cables| P1[RJ45, Fiber, Hubs, Cables]
```

The OSI (Open Systems Interconnection) model is a conceptual framework used to understand network interactions across seven distinct layers. Each layer provides specific services to the layer above it and receives services from the layer below, enabling standardized communication between diverse systems.
