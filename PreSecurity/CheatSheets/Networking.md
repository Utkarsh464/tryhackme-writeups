# Networking Cheat Sheet

## OSI Model Layers
| Layer | Name | PDU | Protocol Examples | Devices |
|-------|------|-----|-------------------|---------|
| 7 | Application | Data | HTTP, DNS, FTP, SMTP | Application, gateway |
| 6 | Presentation | Data | TLS, JPEG, ASCII | Gateway |
| 5 | Session | Data | NetBIOS, RPC | Gateway |
| 4 | Transport | Segment | TCP, UDP | Firewall, Load Balancer |
| 3 | Network | Packet | IP, ICMP, ARP | Router |
| 2 | Data Link | Frame | Ethernet, PPP | Switch, Bridge |
| 1 | Physical | Bit | 10BASE-T, DSL | Hub, Repeater, Cable |

## Common Ports
| Port | Protocol | Service |
|------|----------|---------|
| 20/21 | TCP | FTP |
| 22 | TCP | SSH |
| 23 | TCP | Telnet |
| 25 | TCP | SMTP |
| 53 | TCP/UDP | DNS |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 143 | TCP | IMAP |
| 443 | TCP | HTTPS |
| 445 | TCP | SMB |
| 1433 | TCP | MSSQL |
| 3306 | TCP | MySQL |
| 3389 | TCP | RDP |
| 5432 | TCP | PostgreSQL |
| 8080 | TCP | HTTP-Proxy |
| 8443 | TCP | HTTPS-Alt |

## Protocol Summary
| Protocol | Layer | Transport | Features |
|----------|-------|-----------|----------|
| TCP | 4 (Transport) | N/A | Connection-oriented, reliable, in-order |
| UDP | 4 (Transport) | N/A | Connectionless, fast, no guarantee |
| IP | 3 (Network) | N/A | Addressing, routing, fragmentation |
| ICMP | 3 (Network) | N/A | Error reporting, ping |
| ARP | 2 (Data Link) | N/A | IP → MAC resolution |