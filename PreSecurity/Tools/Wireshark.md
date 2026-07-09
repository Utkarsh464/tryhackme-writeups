# Wireshark

## Purpose
Network protocol analyzer for capturing and inspecting packets in real-time. Used for traffic analysis, incident investigation, and protocol debugging.

## Installation
```bash
sudo apt install wireshark      # Debian/Ubuntu
sudo yum install wireshark      # RHEL/CentOS
choco install wireshark         # Windows (Chocolatey)
```

## Basic Usage
Open Wireshark → Select interface → Start capture → Apply filters → Analyze packets.

```bash
# CLI equivalent
tshark -i eth0 -w capture.pcap
tshark -r capture.pcap -Y "http.request"
```

## Important Commands
- `tcp.port == 80` - Filter HTTP traffic
- `ip.addr == 10.10.10.1` - Filter by IP
- `http.request` or `http.response` - HTTP packets
- `tcp.stream eq 0` - Follow TCP stream
- `icmp` - View ICMP (ping) traffic
- `!arp` - Exclude ARP noise
- `tls.handshake.type == 1` - TLS Client Hello
- `frame contains "pass"` - Search for string in payload

## Typical Workflow
1. Capture traffic on target interface (or load .pcap)
2. Apply display filter to narrow traffic
3. Follow TCP/UDP streams to view session data
4. Export objects (HTTP, SMB) to recover files
5. Use Statistics → Protocol Hierarchy for overview
6. Identify suspicious patterns (port scans, beaconing, exfil)

## Official Documentation
https://www.wireshark.org/docs/