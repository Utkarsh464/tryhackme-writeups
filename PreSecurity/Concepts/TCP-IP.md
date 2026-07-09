# TCP/IP Model

## Definition
The TCP/IP model (Internet Protocol Suite) condenses the OSI 7 layers into **4 layers**: Network Access, Internet, Transport, and Application. It is the practical framework used by the internet. The Internet layer (IP) handles addressing/routing; Transport (TCP/UDP) handles reliability; Application (HTTP, DNS) provides services.

## Why It Matters
TCP/IP is what actually runs the internet. All security tools (Nmap, Wireshark, firewalls) work with TCP/IP headers, ports, and flags. Understanding the TCP handshake, port numbering, and protocol encapsulation is critical for reconnaissance, scanning, and exploitation.

## Where It Appears in the Path
- Network Fundamentals
- How The Web Works

## Prerequisites
- OSI Model basics

## Key Points
- Internet Layer = OSI Layer 3 (Network)
- Transport Layer = OSI Layer 4 (Transport)
- Application Layer = OSI Layers 5-7 combined
- TCP: connection-oriented, reliable, three-way handshake
- UDP: connectionless, faster, no guarantee

## Common Interview Questions
1. What is the TCP three-way handshake?
**Answer:** SYN → SYN-ACK → ACK.
2. How does TCP/IP differ from OSI?
**Answer:** TCP/IP has 4 layers (merging upper layers and lower layers); OSI has 7.
3. What port range do ephemeral ports use?
**Answer:** 49152–65535 (dynamic/private range).

## Further Reading
- RFC 793 (TCP)
- RFC 791 (IP)
- TCP/IP Illustrated (Stevens)