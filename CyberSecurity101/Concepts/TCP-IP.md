# TCP/IP

## Definition
TCP/IP (Transmission Control Protocol / Internet Protocol) is the suite of communication protocols used to interconnect network devices on the Internet. It was developed by the U.S. Department of Defense in the 1970s and remains the foundational protocol stack for modern networking. While the OSI model has 7 layers, TCP/IP is typically described as a 4-layer model: Network Interface, Internet, Transport, and Application.

## Why It Matters
TCP/IP is literally the language of the Internet. Every packet that travels across the global network uses TCP/IP protocols. Understanding TCP/IP is essential for analyzing network traffic, configuring firewalls, troubleshooting connectivity, identifying attacks (SYN floods, IP spoofing, port scans), and understanding how data flows between systems.

## Where It Appears in the Path
TCP/IP is covered in the networking module alongside the OSI model. It is foundational for understanding HTTP, DNS, SSH, FTP, SMB, VPNs (IPsec), firewalls, IDS/IPS, and almost every other network-dependent topic in the path.

## Prerequisites
- Networking fundamentals (MAC/IP addressing)
- OSI model understanding is helpful but not required

## The 4-Layer Model

### Layer 1 — Network Interface (Link Layer)
Maps to OSI Layers 1 and 2. Defines how data is physically transmitted over the network medium (Ethernet, Wi-Fi, fiber). Handles framing, MAC addressing, and error detection. Protocols: Ethernet, PPP, Wi-Fi (802.11), ARP.

### Layer 2 — Internet Layer
Maps to OSI Layer 3. Handles logical addressing and routing of packets between networks. The primary protocol is IP (Internet Protocol), which provides best-effort delivery. Protocols: IPv4, IPv6, ICMP, IGMP, IPsec. Devices: routers.

### Layer 3 — Transport Layer
Maps to OSI Layer 4. Provides end-to-end communication between applications. Two main protocols:
- **TCP**: Reliable, connection-oriented, ordered delivery.
- **UDP**: Unreliable, connectionless, fast delivery.

### Layer 4 — Application Layer
Maps to OSI Layers 5, 6, and 7. Includes application-level protocols: HTTP, HTTPS, DNS, SSH, FTP, SMTP, POP3, IMAP, DHCP, SNMP, TLS/SSL (sometimes considered presentation layer, but in TCP/IP it belongs here).

## IPv4
32-bit address space (approximately 4.3 billion addresses). Written in dotted decimal: `192.168.1.1`. Headers are 20-60 bytes. IPv4 addresses are depleted, driving the adoption of IPv6. Key fields: Source IP, Destination IP, TTL, Protocol, Header Checksum. Supports fragmentation at routers. Private ranges: 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16.

## IPv6
128-bit address space (340 undecillion addresses). Written in hexadecimal colon notation: `2001:0db8:85a3::8a2e:0370:7334`. No NAT needed (every device can have a global address). Headers are fixed at 40 bytes, no checksum (relies on Layer 2), no fragmentation at routers (handled by hosts). Key improvements: built-in IPsec, Neighbor Discovery Protocol (NDP instead of ARP), stateless address autoconfiguration (SLAAC).

## TCP vs UDP

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented (handshake) | Connectionless |
| Reliability | Guaranteed delivery, retransmits | No guarantees |
| Ordering | Preserves byte order | No ordering |
| Flow Control | Sliding window | None |
| Error Checking | Checksum + ACK | Checksum only (optional) |
| Header Size | 20-60 bytes | 8 bytes |
| Speed | Slower (overhead) | Faster |
| Use Cases | Web, email, file transfer, SSH | Streaming, DNS, VoIP, gaming |

## TCP 3-Way Handshake
The process to establish a TCP connection:
1. **SYN**: Client sends a TCP segment with the SYN flag set, an initial sequence number (ISN), and optionally MSS and window scaling options.
2. **SYN-ACK**: Server responds with SYN and ACK flags set, its own ISN, and acknowledges the client's ISN + 1.
3. **ACK**: Client sends an ACK segment acknowledging the server's ISN + 1. The connection is now established.

Connection termination uses a 4-way handshake: FIN → ACK → FIN → ACK.

## TCP Flags
URG (urgent), ACK (acknowledgment), PSH (push), RST (reset), SYN (synchronize), FIN (finish). Understanding flag combinations is crucial for packet filtering and attack detection (e.g., SYN scan, Xmas scan, FIN scan).

## Common Interview Questions
1. **Explain the TCP 3-way handshake in detail.** SYN → SYN-ACK → ACK. Each step establishes sequence numbers, window sizes, and options.
2. **When would you use UDP instead of TCP?** Real-time applications (VoIP, streaming, DNS queries, DHCP) where speed matters more than reliability or where retransmission isn't useful.
3. **What is the difference between IPv4 and IPv6?** Address size (32 vs 128 bits), header complexity, NAT requirement, fragmentation handling, built-in security features.
4. **What is a SYN flood attack and how is it mitigated?** Attacker sends many SYN packets but never completes the handshake, exhausting server resources. Mitigations: SYN cookies, increased backlog queue, rate limiting, firewalls.
5. **What is the TCP sliding window?** Flow control mechanism where the receiver advertises how much data it can accept. The sender transmits up to that window size without waiting for ACKs.
6. **What is the purpose of the TTL field in IP?** Time To Live prevents packets from looping indefinitely. Each router decrements TTL by 1. When TTL reaches 0, the packet is dropped and an ICMP Time Exceeded message is sent.

## Further Reading
- [RFC 793 — TCP](https://tools.ietf.org/html/rfc793)
- [RFC 791 — IP](https://tools.ietf.org/html/rfc791)
- [RFC 8200 — IPv6](https://tools.ietf.org/html/rfc8200)
- _TCP/IP Illustrated_ by W. Richard Stevens
- Cloudflare Learning Center: TCP/IP
