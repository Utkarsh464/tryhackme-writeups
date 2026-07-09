# Module 2: Network Fundamentals — Quick Reference

## Key Concepts
- **OSI Model**: 7 layers — Physical, Data Link, Network, Transport, Session, Presentation, Application
- **TCP/IP Model**: 4 layers — Network Access, Internet, Transport, Application
- **TCP**: Connection-oriented, reliable, sequenced, slower (web, email, FTP)
- **UDP**: Connectionless, fast, no reliability guarantees (streaming, DNS, VoIP)
- **IP Addresses**: IPv4 (32-bit, dotted decimal) and IPv6 (128-bit, hex)
- **Subnetting**: Dividing networks using CIDR notation (e.g., /24 = 255.255.255.0)
- **NAT**: Maps private IPs to public IPs (conserves IPv4, adds security)
- **DHCP**: Dynamic Host Configuration Protocol — DORA (Discover, Offer, Request, Acknowledge)
- **DNS**: Resolves domain names to IP addresses (hierarchical: root → TLD → authoritative)
- **ARP**: Resolves IP to MAC addresses on local networks
- **Routing**: Moving packets between networks using routers and routing protocols (OSPF, BGP)

## Important Ports
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
| 3389 | TCP | RDP |
| 3306 | TCP | MySQL |

## Key Terms
- **Switch**: Layer 2, forwards frames by MAC address
- **Router**: Layer 3, forwards packets by IP address
- **Hub**: Layer 1, broadcasts to all ports
- **VLAN**: Virtual LAN — logical network segmentation
- **VPN**: Encrypted tunnel over public networks
- **MAC Address**: Physical address burned into NIC (48-bit hex)
- **TTL**: Time To Live — prevents packets from looping forever
- **MTU**: Maximum Transmission Unit (typically 1500 bytes)
