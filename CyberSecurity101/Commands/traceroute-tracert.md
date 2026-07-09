# traceroute / tracert

**Traceroute** (Linux/macOS) / **Tracert** (Windows) — a command-line utility for tracing the path packets take from source to destination across an IP network.

## Syntax (Linux/macOS)

```
traceroute [options] <destination>
```

## Syntax (Windows)

```
tracert [options] <destination>
```

## Purpose

Discover the route (series of hops/routers) that packets travel from your machine to a remote host. Used for network diagnostics, identifying latency bottlenecks, and understanding network topology.

## How It Works

Traceroute sends packets with incrementing Time To Live (TTL) values. TTL=1 is dropped by the first router, which sends back an ICMP Time Exceeded message. TTL=2 reaches the second router, and so on, until the destination is reached. Each router's response reveals its IP address and the time taken.

## Common Parameters (Linux traceroute)

| Parameter | Description |
|-----------|-------------|
| `-n` | Numeric output (do not resolve hostnames) |
| `-m <max>` | Maximum TTL (max hops, default 30) |
| `-q <n>` | Number of probes per hop (default 3) |
| `-w <sec>` | Timeout for response (seconds) |
| `-I` | Use ICMP Echo instead of UDP (some networks block UDP) |
| `-T` | Use TCP SYN (port 80 default) |
| `-p <port>` | Destination port for UDP/TCP probes |
| `-4 / -6` | Force IPv4 or IPv6 |

## Common Parameters (Windows tracert)

| Parameter | Description |
|-----------|-------------|
| `-d` | Do not resolve hostnames |
| `-h <hops>` | Maximum hops (default 30) |
| `-w <ms>` | Timeout in milliseconds |

## Examples

```bash
# Basic traceroute
traceroute example.com

# Numeric (skip DNS, much faster)
traceroute -n 8.8.8.8

# Use ICMP instead of UDP
sudo traceroute -I 8.8.8.8

# Use TCP (useful when UDP is filtered)
sudo traceroute -T -p 443 8.8.8.8

# Set maximum hops
traceroute -m 15 10.10.10.1

# IPv6 traceroute
traceroute -6 2001:4860:4860::8888

# Windows tracert (basic)
tracert example.com

# Windows tracert without DNS
tracert -d 8.8.8.8

# Avoid long timeouts with quick scan
traceroute -n -q 1 -w 1 8.8.8.8
```

## Interpreting Output

```
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  gateway (192.168.1.1)  1.234 ms  1.145 ms  1.089 ms
 2  * * *                              ← no response from hop 2
 3  10.10.0.1  12.345 ms  11.234 ms  11.567 ms
 4  72.14.238.232  14.567 ms  14.890 ms  15.123 ms
 5  8.8.8.8  16.456 ms  15.789 ms  16.123 ms
```

- **Hop number:** The router's position in the path
- **IP/hostname:** The responding router
- **Three times:** RTT for each of 3 probes
- **`* * *`** : No response (router may block probes or be configured not to respond)

## Common Mistakes

- Expecting all hops to respond — many routers are configured to not respond to traceroute probes (shown as `*`).
- Using UDP traceroute on networks that only allow TCP — use `-T` (TCP) or `-I` (ICMP).
- Interpreting `*` as a failure — it just means that specific router did not respond; the path still works.
- Not using `-n` — DNS lookups for every hop slow the trace down significantly.
- Assuming symmetric routing — the return path may be completely different from the forward path.
- Running without `sudo` for `-I` or `-T` — ICMP and TCP traceroutes require raw socket access (root).

## Real-World Usage

- **Network troubleshooting:** Identify where packet loss or high latency occurs along a path.
- **Topology discovery:** Map network paths in CTF challenges or penetration testing engagements.
- **CDN analysis:** See which geographic point-of-presence a CDN resolves to.
- **Firewall testing:** Determine which hops are filtering specific protocols.
- **Routing issues:** Identify routing loops, asymmetric paths, or suboptimal routing.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | `traceroute` via apt/yum |
| Windows | Full | `tracert` (pre-installed) |
| macOS | Full | `traceroute` (pre-installed) |

```bash
# Install on Linux
sudo apt install traceroute
```
