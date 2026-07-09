# Networking

## Definition
Computer networking is the practice of connecting computers and devices to share resources and communicate. Networks range from small local area networks (LANs) to the global Internet. Networking involves hardware (routers, switches, hubs, cables), protocols (rules for communication), and addressing schemes (IP addresses, MAC addresses) that enable data transmission between endpoints.

## Why It Matters
Networking is the backbone of all modern computing. Every attack, defense, and security tool operates over a network. Understanding how data flows, how devices discover each other, and where vulnerabilities exist is essential for identifying, exploiting, and defending against network-based threats. Without networking fundamentals, concepts like firewalls, VPNs, and intrusion detection lack context.

## Where It Appears in the Path
Networking is a foundational module early in the Cyber Security 101 path. It underpins every subsequent topic — web security, wireless security, protocol analysis, penetration testing, and incident response all require networking knowledge.

## Prerequisites
- Basic understanding of computers and the Internet
- No prior networking experience required

## LAN vs WAN
- **LAN (Local Area Network)**: Confined to a small geographic area (home, office, building). High speed, low latency, owned by a single organization. Uses switches and Ethernet.
- **WAN (Wide Area Network)**: Spans large geographic areas (cities, countries, continents). Routers connect LANs across WAN links (leased lines, fiber, satellite). The Internet is the largest WAN.
- **MAN (Metropolitan Area Network)**, **PAN (Personal Area Network)**, **CAN (Campus Area Network)** — intermediate categories.

## Network Topologies
- **Bus**: All devices share a single cable. Cheap but single point of failure.
- **Star**: All devices connect to a central switch/hub. Most common in modern LANs.
- **Ring**: Each device connects to two neighbors, forming a ring. Used in FDDI and SONET.
- **Mesh**: Every device connects to every other device. Redundant but expensive (used in WANs).
- **Hybrid**: Combination of topologies (e.g., star-bus, tree).

## Addressing
- **MAC Address (Layer 2)**: 48-bit hardware address burned into the NIC. Unique per device. Used within a LAN segment. Format: `00:1A:2B:3C:4D:5E`.
- **IP Address (Layer 3)**: Logical address assigned to a device on a network. IPv4 is 32-bit (e.g., `192.168.1.1`), IPv6 is 128-bit (e.g., `fe80::1`). IP addresses enable routing across networks.
- **Port Number (Layer 4)**: Identifies specific applications/services on a device (e.g., HTTP=80, HTTPS=443, SSH=22).
- **Socket**: Combination of IP address + port number (e.g., `192.168.1.1:80`).

## Key Protocols
- **ARP (Address Resolution Protocol)**: Resolves IP addresses to MAC addresses on a local network.
- **DHCP (Dynamic Host Configuration Protocol)**: Automatically assigns IP addresses, subnet masks, default gateways, and DNS servers.
- **ICMP (Internet Control Message Protocol)**: Diagnostic and error reporting (e.g., ping, traceroute).
- **NAT (Network Address Translation)**: Maps private IP addresses to a public IP for Internet access.

## Subnetting
Subnetting divides an IP network into smaller subnetworks. It uses a subnet mask (e.g., `255.255.255.0` or `/24`) to distinguish the network portion from the host portion. CIDR notation (Classless Inter-Domain Routing) replaces classful addressing. Example: `192.168.1.0/24` = network `192.168.1.0`, subnet mask `255.255.255.0`, 254 usable hosts.

## Common Interview Questions
1. **What is the difference between a switch and a router?** Switch operates at Layer 2 (data link) and forwards frames based on MAC addresses within a LAN. Router operates at Layer 3 (network) and forwards packets between different networks based on IP addresses.
2. **What is the difference between TCP and UDP?** TCP is connection-oriented, reliable, ordered, with flow control and error recovery. UDP is connectionless, fast, unreliable, no ordering guarantees.
3. **What is a subnet mask and how does it work?** A 32-bit number that masks the IP address to separate network and host portions. The network portion is the bits set to 1; the host portion is bits set to 0.
4. **Explain the 3-way handshake.** SYN → SYN-ACK → ACK. Used by TCP to establish a connection before data transfer.
5. **What is NAT and why is it used?** NAT translates private (RFC 1918) IP addresses to a public IP. Conserves IPv4 addresses and provides a level of obscurity.
6. **What is the OSI model and how does it relate to TCP/IP?** The OSI model has 7 layers (Physical → Application). TCP/IP is a 4-layer model (Network Interface → Internet → Transport → Application) that maps roughly to OSI layers.

## Further Reading
- _Computer Networking: A Top-Down Approach_ by Kurose & Ross
- [Cisco Networking Academy](https://www.netacad.com/)
- [RFC 1180 — TCP/IP Tutorial](https://tools.ietf.org/html/rfc1180)
- Professor Messer Network+ videos (free on YouTube)
- Packet Tracer / GNS3 for hands-on practice
