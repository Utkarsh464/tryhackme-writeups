# Networking Core Protocols — Tasks

## Task 1: TCP and UDP
- **Purpose:** Understand the differences between TCP and UDP, their header structures, and when to use each.
- **Skills:** Protocol comparison, port number identification, three-way handshake analysis.
- **Commands:** None.
- **Theory:** TCP provides reliable, ordered delivery with flow control and error checking, using a three-way handshake (SYN, SYN-ACK, ACK) to establish connections. UDP is connectionless and faster but provides no delivery guarantees. Common ports: TCP/80 (HTTP), TCP/443 (HTTPS), UDP/53 (DNS), UDP/67-68 (DHCP).

## Task 2: Internet Protocol (IP) and ICMP
- **Purpose:** Understand the IP packet structure and how ICMP supports diagnostics.
- **Skills:** IP header field interpretation, ICMP type/code mapping.
- **Commands:** None.
- **Theory:** The IP header includes source/destination addresses, TTL, protocol number, and fragmentation flags. ICMP messages (e.g., echo request/reply, destination unreachable, TTL exceeded) are encapsulated in IP packets and used by tools like ping and traceroute.

## Task 3: DNS and DHCP
- **Purpose:** Learn how DNS translates domain names to IP addresses and how DHCP assigns network configuration automatically.
- **Skills:** DNS record type identification, DHCP DORA process understanding.
- **Commands:** None.
- **Theory:** DNS uses a hierarchical namespace with root servers, TLD servers, and authoritative nameservers. Common record types: A, AAAA, CNAME, MX, NS. DHCP uses the DORA process (Discover, Offer, Request, Acknowledge) to assign IP addresses, subnet masks, gateways, and DNS servers.

## Task 4: HTTP and ARP
- **Purpose:** Understand the HTTP request-response cycle and the role of ARP in local network communication.
- **Skills:** HTTP method identification, status code interpretation, ARP resolution understanding.
- **Commands:** None.
- **Theory:** HTTP is a text-based protocol where clients send requests (GET, POST, etc.) and servers respond with status codes (200 OK, 404 Not Found, 500 Server Error). ARP resolves IP addresses to MAC addresses within a local network segment.
