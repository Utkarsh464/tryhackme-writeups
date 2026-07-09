# Concepts: Packets and Frames

## 1. TCP Segment
TCP segments have a 20-60 byte header containing source/destination ports, sequence numbers (for ordering), acknowledgment numbers, control flags (SYN, ACK, FIN, RST), window size (flow control), and checksum (error detection). TCP is connection-oriented and guarantees delivery.

## 2. The TCP Three-Way Handshake
A connection establishment process: SYN (client synchronizes), SYN-ACK (server acknowledges), ACK (client confirms). This ensures both sides are ready to communicate and synchronizes sequence numbers for reliable data transfer.

## 3. UDP Datagram
UDP has an 8-byte header: source port, destination port, length, and checksum. It is connectionless, has no sequencing or retransmission, and is faster than TCP. Used for DNS, DHCP, streaming media, and online gaming where speed is prioritized over reliability.

## 4. IP Packet Header
The IP header (20-60 bytes) includes: version (4), IHL, ToS, total length, identification (for fragmentation), flags (MF, DF), fragment offset, TTL (decremented at each hop), protocol, header checksum, and source/destination IP addresses.

## 5. TTL (Time to Live)
A field in the IP header that prevents infinite routing loops. Each router decrements TTL by 1. When TTL reaches 0, the packet is discarded and an ICMP Time Exceeded message is sent back. Typical starting values are 64, 128, or 255.

## 6. Ethernet Frame Structure
An Ethernet frame has: preamble (7 bytes for synchronization), SFD (1 byte), destination MAC (6 bytes), source MAC (6 bytes), EtherType (2 bytes, identifying payload protocol), payload (46-1500 bytes), and FCS (4 bytes CRC). The minimum payload of 46 bytes ensures collision detection works properly.

## 7. MTU (Maximum Transmission Unit)
The largest size a data unit can be for a given network interface. Standard Ethernet MTU is 1500 bytes. If a packet exceeds MTU, it is fragmented at Layer 3. Path MTU discovery finds the smallest MTU along a route to avoid fragmentation.

## 8. Encapsulation and De-encapsulation
Encapsulation wraps data with headers as it moves down the protocol stack. De-encapsulation removes headers as data moves up the stack at the receiving end. Each layer only processes its own header, treating the rest as payload.
