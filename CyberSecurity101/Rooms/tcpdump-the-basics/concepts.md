# Tcpdump: The Basics — Concepts

## Tcpdump
A powerful command-line packet analyzer that captures and displays network packets. Uses libpcap as its capture engine. Available on most Unix-like systems.

## BPF (Berkeley Packet Filter)
A syntax for filtering packets at the kernel level. Tcpdump compiles BPF expressions into pseudo-machine code for efficient filtering. Filters can match on hosts, ports, protocols, and packet properties.

## Promiscuous Mode
A network interface mode where the interface captures all packets it sees, not just those addressed to it. Required for effective network monitoring. Requires root privileges.

## pcap (Packet Capture)
A file format for storing captured network packets. Files use the .pcap or .pcapng extension. Compatible with Wireshark, Tcpdump, and many other analysis tools.

## Verbosity Levels
Tcpdump supports multiple verbosity levels controlled by the `-v` flag. More v's progressively add detail: TTL, IP ID, protocol-specific options, and checksum information.

## Offline Analysis
Analyzing previously captured traffic from a pcap file rather than capturing live traffic. Useful for forensic analysis, incident response, and sharing captures without risk of altering live environments.
