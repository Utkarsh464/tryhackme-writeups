# tcpdump

**TCP Dump** — a powerful command-line packet capture and analysis tool that uses libpcap.

## Syntax

```
tcpdump [options] [expression]
```

## Purpose

Capture and display network packets on a network interface. Lightweight and scriptable, it is the standard tool for packet capture on Unix systems. Essential for network debugging, intrusion detection analysis, and traffic monitoring.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-i <iface>` | Interface to capture on |
| `-n` | Do not resolve hostnames |
| `-nn` | Do not resolve hostnames or ports |
| `-v`, `-vv`, `-vvv` | Verbosity levels |
| `-c <count>` | Capture N packets then stop |
| `-s <snaplen>` | Snap length (bytes to capture per packet; `-s 0` = full) |
| `-w <file>` | Write raw packets to a file |
| `-r <file>` | Read packets from a file |
| `-X` | Show hex and ASCII dump |
| `-A` | Show ASCII only |
| `-e` | Show link-layer header (MAC addresses) |
| `-q` | Quiet output (less protocol information) |
| `-S` | Print absolute sequence numbers |

## BPF Filter Expressions

| Expression | Description |
|------------|-------------|
| `host 10.10.10.1` | Traffic to/from a host |
| `src 10.10.10.1` | Traffic from a source |
| `dst 10.10.10.1` | Traffic to a destination |
| `port 80` | Traffic on a specific port |
| `tcp`, `udp`, `icmp` | Protocol filter |
| `and`, `or`, `not` | Boolean operators |
| `tcp port 80 and host 10.10.10.1` | Combined filters |
| `broadcast` | Broadcast traffic |
| `tcp[13] & 2 != 0` | TCP SYN packets only (bitwise match on flags) |

## Examples

```bash
# Capture on an interface
sudo tcpdump -i eth0

# Capture with no name resolution, show hex
sudo tcpdump -i eth0 -nn -X

# Capture HTTP traffic to a specific host
sudo tcpdump host 10.10.10.1 and port 80 -nn

# Save capture to a file
sudo tcpdump -i eth0 -w capture.pcap -c 1000

# Read a capture file
tcpdump -r capture.pcap -nn

# Read with verbose protocol output
tcpdump -r capture.pcap -vv

# Capture only SYN packets
sudo tcpdump -i eth0 'tcp[13] & 2 != 0'

# Capture DHCP traffic
sudo tcpdump -i eth0 port 67 or port 68

# Filter by MAC address
sudo tcpdump ether host aa:bb:cc:dd:ee:ff
```

## Common Mistakes

- Capturing without sudo — raw packet capture requires root privileges on Linux.
- Forgetting `-n` or `-nn` — DNS lookups for every packet slow down capture significantly.
- Using `-s 0` on busy networks — capturing full packets uses a lot of disk space. Default (262144 bytes) is usually excessive.
- Running in production without careful filters — tcpdump can generate huge files and impact performance.
- Not using `-w` for large captures — pipe raw data to a file and analyze later instead of trying to read real-time output.

## Real-World Usage

- **Incident response:** Capture live traffic on a compromised host to analyze C2 communication.
- **Network debugging:** Verify that packets are reaching a destination and check for retransmissions.
- **CTF challenges:** Analyze PCAP files for credentials, flags, or hidden data.
- **Protocol reverse engineering:** Inspect unknown protocols by capturing traffic between a client and server.
- **IDS/IPS validation:** Confirm that detection systems see the same traffic you do.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed on most distributions |
| Windows | Limited | Via WinPcap/Npcap or WSL |
| macOS | Full | Pre-installed, based on libpcap |

```bash
# Install on Linux
sudo apt install tcpdump
```
