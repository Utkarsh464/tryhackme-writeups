# wireshark / tshark

**Wireshark** — a GUI-based network protocol analyzer for capturing and inspecting network traffic in real time. **tshark** is its command-line counterpart.

## Syntax (GUI)

```
wireshark [options] [file.pcap]
```

## Syntax (CLI)

```
tshark [options] [file.pcap]
```

## Purpose

Capture live network traffic and analyze it at the packet level. Used for troubleshooting network issues, analyzing protocols, detecting malicious activity, and learning how network protocols work. Essential for network forensics and CTF challenges involving packet capture (PCAP) files.

## Common Parameters (tshark CLI)

| Parameter | Description |
|-----------|-------------|
| `-i <interface>` | Capture interface |
| `-r <file>` | Read from a PCAP file |
| `-w <file>` | Write output to a file |
| `-Y <filter>` | Display filter expression |
| `-f <filter>` | Capture filter (BPF syntax) |
| `-c <count>` | Stop after capturing N packets |
| `-T fields` | Print specific fields |
| `-e <field>` | Extract field (e.g., `-e ip.src`) |
| `-z <stat>` | Generate statistics |
| `-q` | Quiet mode (suppress packet output) |
| `-V` | Verbose (full protocol tree) |

## Wireshark GUI Features

- **Display Filters:** `http`, `tcp.port==80`, `ip.addr==10.10.10.1`, `dns`, `tls.handshake.type==1`
- **Follow TCP Stream:** Right-click a TCP packet → Follow → TCP Stream (reconstructs conversation)
- **Statistics:** Analyze → Protocol Hierarchy, Conversations, Endpoints
- **Color Coding:** Default colors highlight different protocols
- **Export Objects:** File → Export Objects → HTTP/SMB/TFTP (extract transferred files)

## Examples

```bash
# Capture on interface eth0
sudo tshark -i eth0

# Read a PCAP file and apply display filter
tshark -r capture.pcap -Y "http.request"

# Extract all HTTP hosts from a PCAP
tshark -r capture.pcap -Y "http.host" -T fields -e http.host

# Display source/destination IPs and ports
tshark -r capture.pcap -T fields -e ip.src -e ip.dst -e tcp.srcport -e tcp.dstport

# Follow and print a TCP stream
tshark -r capture.pcap -z follow,tcp,ascii,0

# Capture 100 packets to a file
sudo tshark -i eth0 -c 100 -w output.pcap

# Show HTTP requests with response status
tshark -r capture.pcap -Y "http" -T fields -e http.request.method -e http.response.code -e http.host
```

## Common Mistakes

- Capturing on the wrong interface — use `tshark -D` or `wireshark -D` to list interfaces first.
- Not running with sudo on Linux — raw packet capture requires elevated privileges.
- Using capture filters instead of display filters for complex expressions — capture filters use BPF syntax (limited), display filters use Wireshark's rich expression language.
- Keeping the capture running indefinitely without a ring buffer — the file grows until it fills the disk.
- Overlooking TLS decryption — use `(pre)-master-secret` log files from browsers or servers to decrypt HTTPS.

## Real-World Usage

- **Network forensics:** Analyze PCAPs from compromised networks to trace attacker activity.
- **CTF packet analysis:** Extract flags, credentials, or hidden files from PCAP files.
- **Protocol analysis:** Understand how DHCP, ARP, DNS, TCP handshakes work at the byte level.
- **Malware analysis:** Determine C2 communication patterns and data exfiltration.
- **Troubleshooting:** Diagnose slow connections, packet loss, or misconfigured services.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | `sudo apt install wireshark tshark` |
| Windows | Full | Installer from wireshark.org |
| macOS | Full | Installer or `brew install wireshark` |

```bash
# Install on Linux
sudo apt install wireshark tshark
sudo usermod -aG wireshark $USER  # non-root capture
```
