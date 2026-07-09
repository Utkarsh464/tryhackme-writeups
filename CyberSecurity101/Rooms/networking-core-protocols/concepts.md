# Networking Core Protocols — Concepts

## TCP (Transmission Control Protocol)
A connection-oriented transport protocol that provides reliable, ordered delivery. Uses a three-way handshake (SYN, SYN-ACK, ACK) to establish connections and sequence numbers to ensure ordered delivery.

## UDP (User Datagram Protocol)
A connectionless transport protocol with minimal overhead. Provides no guarantees of delivery, ordering, or error recovery. Ideal for real-time applications like streaming and VoIP.

## IP (Internet Protocol)
The network layer protocol responsible for addressing and routing packets between hosts. IPv4 uses 32-bit addresses; IPv6 uses 128-bit addresses.

## ICMP (Internet Control Message Protocol)
Used for error reporting and network diagnostics. Common message types include echo request/reply (ping), destination unreachable, and TTL exceeded.

## ARP (Address Resolution Protocol)
Maps an IPv4 address to a MAC address on a local network. ARP broadcasts a request and stores responses in the ARP cache.

## DNS (Domain Name System)
Resolves human-readable domain names to IP addresses. Uses a hierarchical namespace with root, TLD, and authoritative servers.

## DHCP (Dynamic Host Configuration Protocol)
Automatically assigns IP addresses and network configuration (subnet mask, gateway, DNS) to devices. Uses the DORA process.

## HTTP (Hypertext Transfer Protocol)
The application-layer protocol for web communication. Uses methods like GET and POST with status codes indicating success or failure.
