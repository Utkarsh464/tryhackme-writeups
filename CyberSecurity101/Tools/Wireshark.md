# Wireshark

## Purpose
Wireshark is the world's most widely used network protocol analyzer. It captures live network traffic and provides deep inspection of hundreds of protocols. Wireshark is essential for network troubleshooting, protocol analysis, security incident investigation, and understanding network communications. Originally called Ethereal, it is developed and maintained by the Wireshark community under the GNU GPL license.

## Installation
Wireshark is pre-installed on Kali Linux. On other systems:
```bash
# Debian/Ubuntu
sudo apt update && sudo apt install wireshark
# During install, answer "Yes" to allow non-root users to capture packets

# Red Hat/CentOS/Fedora
sudo dnf install wireshark

# Arch Linux
sudo pacman -S wireshark-qt

# macOS
brew install --cask wireshark

# Windows
Download from https://www.wireshark.org/download.html

# Add user to wireshark group (Linux)
sudo usermod -aG wireshark $USER
# Log out and back in for group membership to take effect
```

## Basic Usage
Launch Wireshark with GUI or use TShark (CLI version):
```bash
# Interactive GUI
wireshark

# List available interfaces
tshark -D

# Capture on interface eth0
wireshark -i eth0
# or via CLI
tshark -i eth0 -w capture.pcap
```

Select the network interface to capture from, then click the blue shark fin button to start. Apply display filters to narrow down traffic. Right-click packets for conversation filtering and follow streams.

## Important Features
- **Capture Filters** - Berkeley Packet Filter (BPF) syntax applied before capture: `host 10.10.10.10`, `port 80 or port 443`, `not arp`
- **Display Filters** - Applied after capture to show/hide packets: `http.request`, `tcp.port == 443`, `ip.addr == 192.168.1.1`, `dns.qry.name contains "google"`
- **Follow TCP/UDP/TLS Stream** - Reassemble and view the full application-layer conversation (right-click packet > Follow > TCP Stream)
- **Statistics Menu** - Protocol Hierarchy, Conversations, Endpoints, IO Graph, Flow Graph, IPv4/IPv6 Statistics
- **Coloring Rules** - Color-code packets by protocol or custom rules for rapid visual analysis
- **Expert Info** - Automatically identifies errors, warnings, notes, and chats in the capture
- **Name Resolution** - Resolve MAC addresses to vendors, IP addresses to DNS names, and ports to service names
- **Export Objects** - Extract files transferred over HTTP, SMB, TFTP, and other protocols

## Typical Workflow
1. Select the appropriate network interface for capture
2. Apply a capture filter if traffic volume is high (e.g., `host 10.10.10.10`)
3. Start capture and reproduce the network issue or attack
4. Stop capture and save the file as `.pcapng`
5. Apply display filters to isolate relevant traffic
6. Use Statistics > Protocol Hierarchy to understand traffic composition
7. Follow TCP/UDP streams to view application-layer data
8. Check Expert Info for anomalies
9. Extract indicators of compromise (IPs, domains, file hashes)
10. Export relevant packets or objects for evidence

## Advantages
- Deep inspection of 3,000+ protocols
- Cross-platform with consistent interface
- Powerful display filter language
- Active community and frequent updates
- Free and open-source with no limitations
- Extensive file format support (pcap, pcapng, snoop, etc.)
- Rich statistics and visualization capabilities

## Limitations
- Cannot capture on wireless interfaces in monitor mode on all adapters
- Large captures consume significant memory and CPU
- Cannot decrypt modern TLS without pre-shared keys or key log files
- Capturing on high-throughput links (10Gbps+) requires specialized hardware
- BPF capture filters can be complex to write correctly
- Decryption of encrypted traffic requires key material

## Industry Use
Wireshark is used by network engineers for troubleshooting, security analysts for incident response and malware traffic analysis, penetration testers for credential harvesting and protocol analysis, and developers for debugging network protocols. It is a standard tool in every SOC analyst's toolkit.

## Official Documentation
- Official Site: https://www.wireshark.org
- Documentation: https://www.wireshark.org/docs/
- Display Filters: https://www.wireshark.org/docs/dfref/
- Sample Captures: https://wiki.wireshark.org/SampleCaptures
- GitHub: https://github.com/wireshark/wireshark
