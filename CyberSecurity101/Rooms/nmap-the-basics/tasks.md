# Nmap: The Basics — Tasks

## Task 1: Host Discovery
- **Purpose:** Identify which hosts on a network are alive and responding.
- **Skills:** Ping sweep, list scan, target specification.
- **Commands:** `nmap -sn 192.168.1.0/24`, `nmap -sL 192.168.1.0/24`, `nmap -PS22,80 192.168.1.0/24`
- **Theory:** `-sn` performs a ping sweep (ICMP echo, TCP SYN to 443 and 80, and ICMP timestamp). List scan `-sL` simply lists targets without sending probes. TCP SYN ping `-PS` sends SYN packets to specified ports.

## Task 2: Port Scanning Techniques
- **Purpose:** Enumerate open ports on a target to understand its attack surface.
- **Skills:** SYN scan, TCP connect scan, port ranges, scan types.
- **Commands:** `nmap -sS 192.168.1.1`, `nmap -sT 192.168.1.1`, `nmap -sU 192.168.1.1`, `nmap -p 1-1000 192.168.1.1`, `nmap -p- 192.168.1.1`
- **Theory:** SYN scan `-sS` sends SYN packets and observes responses (half-open, default). Connect scan `-sT` completes the TCP handshake. UDP scan `-sU` is slower and less reliable. Port ranges use `-p` with hyphen or comma notation.

## Task 3: Service and OS Detection
- **Purpose:** Determine the operating system and running service versions on discovered ports.
- **Skills:** Version detection, OS fingerprinting.
- **Commands:** `nmap -sV 192.168.1.1`, `nmap -O 192.168.1.1`, `nmap -A 192.168.1.1`
- **Theory:** `-sV` probes open ports to determine service versions. `-O` uses TCP/IP stack fingerprinting to guess the OS. `-A` enables both along with traceroute and NSE scripts.

## Task 4: NSE Scripts
- **Purpose:** Extend Nmap's functionality using the Nmap Scripting Engine for enumeration and vulnerability scanning.
- **Skills:** Script selection by category, script argument passing.
- **Commands:** `nmap -sC 192.168.1.1`, `nmap --script=default 192.168.1.1`, `nmap --script=vuln 192.168.1.1`, `nmap --script=http-enum 192.168.1.1`
- **Theory:** NSE scripts are organized by category: default, safe, intrusive, vuln, exploit, discovery, etc. `-sC` runs all default scripts. Use `--script` with category names or script paths to select specific scripts.

## Task 5: Output Formats
- **Purpose:** Save scan results in formats suitable for reporting and further analysis.
- **Skills:** Output flags, format selection.
- **Commands:** `nmap -oN scan.txt 192.168.1.1`, `nmap -oX scan.xml 192.168.1.1`, `nmap -oG scan.gnmap 192.168.1.1`, `nmap -oA scan 192.168.1.1`
- **Theory:** `-oN` writes normal format, `-oX` writes XML, `-oG` writes grepable, and `-oA` outputs all formats. XML is most useful for integration with other tools.
