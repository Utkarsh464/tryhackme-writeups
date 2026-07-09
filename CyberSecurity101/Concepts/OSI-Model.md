# OSI Model

## Definition
The Open Systems Interconnection (OSI) model is a conceptual framework developed by ISO that standardizes the functions of a telecommunication or computing system into seven abstraction layers. Each layer serves a specific purpose and communicates only with the layers directly above and below it. The model enables interoperability between different systems and protocols by defining clear interfaces.

## Why It Matters
The OSI model is the universal language for describing network communication. Security professionals use it to identify which layer an attack targets, where to deploy defensive controls, and how to analyze network traffic. Understanding the OSI model helps isolate problems — is it a physical cable issue (Layer 1), a routing problem (Layer 3), or an application vulnerability (Layer 7)?

## Where It Appears in the Path
The OSI model is introduced in the networking fundamentals module. It provides the framework for understanding subsequent topics: TCP/IP (Layer 4), firewalls (Layers 3-7), IDS/IPS (Layers 2-7), web security (Layer 7), wireless security (Layers 1-2), and VPNs (Layers 2-3).

## Prerequisites
- Basic networking concepts (IP addresses, ports)
- Understanding the OSI model requires no prior deep technical knowledge

## The 7 Layers (Bottom to Top)

### Layer 1 — Physical
Deals with the physical transmission of raw bits over a communication channel. Defines hardware specifications: cables (copper, fiber), connectors, voltages, signaling (electrical, optical, radio), and data rates. Devices: hubs, repeaters, modems, network interface cards (NICs). Attacks: cable tapping, electromagnetic interference, physical destruction.

### Layer 2 — Data Link
Provides node-to-node data transfer, framing, error detection/correction, and flow control. Organizes bits into frames (typically 1500 bytes for Ethernet). Uses MAC addresses (48-bit) to identify devices on the same network segment. The LLC (Logical Link Control) and MAC (Media Access Control) sublayers handle multiplexing and medium access. Devices: switches, bridges. Protocols: Ethernet, PPP, ARP (ARP is often considered Layer 2.5). Attacks: MAC flooding, ARP spoofing, STP manipulation, VLAN hopping.

### Layer 3 — Network
Handles logical addressing, routing, and packet forwarding across networks. Encapsulates segments into packets, determines the best path using routing protocols, and handles fragmentation/reassembly. Devices: routers, Layer 3 switches. Protocols: IP (IPv4, IPv6), ICMP, OSPF, BGP, RIP. Attacks: IP spoofing, routing table poisoning, ICMP redirect, Smurf attack.

### Layer 4 — Transport
Provides end-to-end communication, reliability, flow control, and multiplexing between applications on different hosts. Segments data from the session layer and manages connection establishment/teardown. Protocols: TCP (connection-oriented, reliable), UDP (connectionless, fast), SCTP. Key concepts: ports (0-65535), sequence numbers, acknowledgments, windowing, TCP 3-way handshake. Attacks: SYN flood, port scanning, session hijacking.

### Layer 5 — Session
Manages sessions (dialogues) between applications. Handles session establishment, maintenance, authentication, and termination. Provides checkpointing and recovery — if a session is interrupted, it can resume from the last checkpoint. Protocols: NetBIOS, RPC, SMB, NFS, SSL/TLS handshake (sometimes considered Session layer). Attacks: session hijacking (once established), RPC exploitation.

### Layer 6 — Presentation
Translates data between the application layer and the network. Handles data formatting, encryption, compression, and encoding conversions (ASCII/EBCDIC, JPEG, GIF, MPEG, TLS/SSL encryption). It ensures data sent by one application is readable by another. Attacks: character encoding exploits (Unicode attacks), compression-based attacks (CRIME).

### Layer 7 — Application
The closest layer to the end user. Provides network services directly to applications. Defines protocols for specific data exchange: web browsing (HTTP/HTTPS), email (SMTP, POP3, IMAP), file transfer (FTP, SFTP), DNS, SSH, DHCP. This is where user interaction happens. Attacks: SQL injection, XSS, buffer overflows, application logic flaws, phishing.

## The Mnenomic
**Please Do Not Throw Sausage Pizza Away** (Physical, Data Link, Network, Transport, Session, Presentation, Application) — from bottom to top.
**All People Seem To Need Data Processing** — from top to bottom.

## Common Interview Questions
1. **Why is the OSI model important?** It standardizes network communication into layers, enabling interoperability, modular development, and simplified troubleshooting.
2. **What happens at each layer when you visit a website?** Application (HTTP request) → Presentation (TLS encryption) → Session (TLS handshake) → Transport (TCP SYN to port 443) → Network (IP routing) → Data Link (Ethernet frame with MAC) → Physical (electrical signals).
3. **What layer does a firewall operate at?** Packet-filter firewalls (Layer 3-4), stateful firewalls (Layer 3-4), application firewalls (Layer 7, specifically inspecting HTTP/DNS/etc).
4. **At which layer does encryption occur?** Primarily Layer 6 (Presentation), though TLS is often described as operating between Layers 4 and 5 (Transport and Session). IPsec operates at Layer 3.
5. **What is the difference between a hub, switch, and router in OSI terms?** Hub = Layer 1 (repeats signals), Switch = Layer 2 (forwards by MAC), Router = Layer 3 (forwards by IP).
6. **What is encapsulation?** Each layer adds its own header (and sometimes trailer) to the data from the layer above. Application data → TCP header → IP header → Ethernet header/trailer.

## Further Reading
- [ISO/IEC 7498-1 (the OSI Model standard)](https://www.iso.org/standard/20269.html)
- _Computer Networks_ by Andrew Tanenbaum
- [OSI Model on Cloudflare Learning Center](https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/)
- Professor Messer Network+ Layer videos
