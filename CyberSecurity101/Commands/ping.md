# ping

**Packet Internet Groper** — a command-line utility for testing network connectivity to a host by sending ICMP Echo Request packets.

## Syntax

```
ping [options] <destination>
```

## Purpose

Verify whether a remote host is reachable and measure round-trip time (RTT). The most fundamental network troubleshooting tool — used to check connectivity, DNS resolution, packet loss, and network latency.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-c <count>` | Stop after sending N packets (Linux) |
| `-n` | Numeric output (do not resolve hostnames) |
| `-i <interval>` | Interval between packets (seconds, default 1) |
| `-s <size>` | Packet size in bytes (default 56, +28 ICMP header = 64) |
| `-t <ttl>` | Set Time To Live |
| `-W <timeout>` | Time to wait for response (seconds) |
| `-f` | Flood mode (root only, sends packets as fast as possible) |
| `-q` | Quiet mode (only show summary) |
| `-D` | Print timestamp before each output line |
| `-4 / -6` | Force IPv4 or IPv6 |

## Examples

```bash
# Basic ping (Linux: continuous until Ctrl+C)
ping 10.10.10.1

# Ping with count (stop after 5 packets)
ping -c 5 10.10.10.1

# Ping with specific packet size
ping -c 3 -s 1500 10.10.10.1

# Numeric output (skip DNS resolution)
ping -n -c 4 10.10.10.1

# Ping with 0.5 second interval
ping -c 10 -i 0.5 10.10.10.1

# Flood ping (root only — tests network performance)
sudo ping -f -c 1000 10.10.10.1

# Quiet mode — only show summary statistics
ping -c 10 -q 10.10.10.1

# Ping with timeout
ping -c 1 -W 2 10.10.10.1

# Set TTL
ping -c 1 -t 10 example.com

# Ping IPv6 address
ping -6 2001:db8::1
```

## Interpreting Output

```
PING 10.10.10.1 (10.10.10.1) 56(84) bytes of data.
64 bytes from 10.10.10.1: icmp_seq=1 ttl=64 time=0.523 ms
64 bytes from 10.10.10.1: icmp_seq=2 ttl=64 time=0.457 ms

--- 10.10.10.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 0.457/0.490/0.523/0.033 ms
```

- **icmp_seq** — sequence number (gaps = packet loss)
- **ttl** — Time To Live remaining (decrements per hop)
- **time** — round-trip time in milliseconds
- **packet loss** — percentage of lost packets
- **rtt** — min/average/max/standard deviation of response times

## Common Mistakes

- Using ping on Windows vs Linux — Windows defaults to 4 packets and stops; Linux pings indefinitely. Use `-c` on Linux for count-limited ping.
- Expecting ping to work on all hosts — many systems block ICMP in firewalls. A host may be up but not responding to ping.
- Interpreting packet loss as network failure — high latency or congestion can cause packet loss.
- Flooding without root (`-f`) — requires elevated privileges.
- Testing with default packet size — path MTU issues may only appear with larger packets. Use `-s 1472` to test for MTU problems.
- Using ping for latency-sensitive applications — ICMP may have different priority than TCP/UDP traffic on network equipment.

## Real-World Usage

- **Basic connectivity check:** `ping 8.8.8.8` — the first test when troubleshooting network issues.
- **DNS validation:** `ping google.com` succeeds but `ping 8.8.8.8` fails — DNS resolution problem.
- **CTF challenges:** Determine if a target is online, scan for live hosts in a subnet (`for i in {1..254}; do ping -c 1 10.10.10.$i & done`).
- **Latency measurement:** Compare RTT to different hosts to identify network bottlenecks.
- **Packet loss monitoring:** Continuous ping to check connection stability (run in background, analyze output).

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (iputils-ping) |
| Windows | Full | Pre-installed, different behavior (4 packets default, `-n` for count, `-t` for continuous) |
| macOS | Full | Pre-installed (BSD ping, similar to Linux) |

```bash
# Install on Linux
sudo apt install iputils-ping
```
