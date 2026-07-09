# Tasks: Packets and Frames

## Task 1: TCP Segment
**Purpose:** Learn the structure of a TCP segment.

**Skills:** Transport layer protocol analysis.

**Theory:** TCP (Transmission Control Protocol) provides reliable, connection-oriented communication. Its segment header includes source/destination ports, sequence and acknowledgment numbers, flags (SYN, ACK, FIN, RST, PSH, URG), window size, and checksum. The three-way handshake establishes a connection.

**Commands:** N/A

---

## Task 2: UDP Datagram
**Purpose:** Understand the simpler UDP header.

**Skills:** Transport layer comparison.

**Theory:** UDP (User Datagram Protocol) is a connectionless protocol with minimal overhead. Its header is only 8 bytes: source port, destination port, length, and checksum. UDP is used for real-time applications like DNS, VoIP, and video streaming where speed matters more than reliability.

**Commands:** N/A

---

## Task 3: IP Packet
**Purpose:** Learn the fields in an IP packet header.

**Skills:** Network layer protocol analysis.

**Theory:** The IP packet header includes version (IPv4/IPv6), IHL, type of service, total length, identification, flags, fragment offset, TTL (Time to Live), protocol (TCP=6, UDP=17), header checksum, and source/destination IP addresses. TTL prevents packets from looping endlessly.

**Commands:** N/A

---

## Task 4: Ethernet Frame
**Purpose:** Understand Ethernet frame structure.

**Skills:** Data link layer analysis.

**Theory:** The Ethernet frame includes a preamble, destination MAC, source MAC, EtherType (identifies the upper-layer protocol, e.g., 0x0800 for IPv4), payload (46-1500 bytes), and FCS (Frame Check Sequence) for error detection. The payload maximum is determined by the MTU.

**Commands:** N/A

---

## Task 5: Encapsulation Process
**Purpose:** Understand how data is wrapped at each layer.

**Skills:** Protocol stack understanding.

**Theory:** Encapsulation wraps each layer's data with its own header. Application data → TCP header (segment) → IP header (packet) → Ethernet header (frame) → bits. Each layer adds its header as data moves down the stack. The receiving device reverses this process (de-encapsulation).

**Commands:** N/A

---
