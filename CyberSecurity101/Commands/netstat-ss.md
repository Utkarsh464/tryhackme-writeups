# netstat / ss

**Network Statistics** — command-line utilities for displaying network connections, routing tables, interface statistics, and more. `netstat` is legacy; `ss` is its modern replacement on Linux.

## Syntax (ss — modern Linux)

```
ss [options]
```

## Syntax (netstat — cross-platform)

```
netstat [options]
```

## Purpose

View active network connections (TCP, UDP), listening ports, routing tables, and network statistics. Essential for identifying which services are running, finding open ports, and diagnosing network issues.

## Common Parameters (ss — modern Linux)

| Parameter | Description |
|-----------|-------------|
| `-t` | TCP connections |
| `-u` | UDP connections |
| `-l` | Listening sockets only |
| `-n` | Numeric (no service name resolution) |
| `-p` | Show process using the socket |
| `-a` | All sockets (listening + established) |
| `-r` | Resolve hostnames |
| `-s` | Print summary statistics |
| `-o` | Show timer information |
| `-4` | IPv4 only |
| `-6` | IPv6 only |
| `state <state>` | Filter by state (e.g., `state established`) |

## Common Parameters (netstat — cross-platform)

| Parameter | Description |
|-----------|-------------|
| `-a` | All connections and listening ports |
| `-t` | TCP connections |
| `-u` | UDP connections |
| `-l` | Listening sockets |
| `-n` | Numeric (no hostname/service resolution) |
| `-p` | Show PID and program name (Linux) |
| `-r` | Display routing table |
| `-i` | Network interface statistics |
| `-s` | Summary statistics per protocol |
| `-c` | Continuous mode (refresh) |

## Examples

```bash
# Show all listening TCP ports (ss)
ss -tln

# Show all listening TCP ports (netstat)
netstat -tln

# Show all connections with process info (ss)
ss -tulnp

# Show all connections with process info (netstat)
sudo netstat -tulnp

# Show established connections
ss -tun state established

# Show summary statistics
ss -s

# Show routing table (netstat)
netstat -rn

# Show network interface statistics (netstat)
netstat -i

# Watch connections in real-time
watch -n 2 'ss -tln'

# Filter by port
ss -tln sport = :80 or dport = :80

# Show sockets for a specific process
ss -tlnp | grep nginx

# Show Unix domain sockets
ss -x

# Show all sockets with timers
ss -tlnpo
```

## Key Differences: ss vs netstat

| Feature | ss | netstat |
|---------|----|---------|
| Speed | Faster (reads from /proc directly) | Slower |
| Installation | Pre-installed (iproute2) | Requires net-tools package |
| Filters | Advanced (by state, port, process) | Basic |
| Output | More detailed | Familiar layout |
| Maintained | Yes (modern) | No (deprecated on Linux) |

## Common Mistakes

- Using `netstat` without `-n` — DNS and service lookups slow the output significantly.
- Forgetting `sudo` — `-p` (show PID/program) requires root to see all processes.
- Using `netstat` on modern Linux when `ss` is preferred — `ss` is faster and more powerful.
- Not filtering output — on a busy server, `netstat -a` produces hundreds of lines. Use `-l` for listening only.
- Confusing listening ports with established connections — `-l` shows only listeners; `-a` includes both.

## Real-World Usage

- **Port enumeration:** Identify which services are listening on a machine — critical for initial recon.
- **CTF challenges:** Find backdoor listeners, identify suspicious connections, enumerate services.
- **Incident response:** Check for outbound connections to malicious IPs (C2 traffic).
- **Troubleshooting:** Verify a service is listening on the expected port.
- **Process-to-port mapping:** Identify which PID is using a specific port (`ss -tlnp`).

## Compatibility

| OS | Tool | Notes |
|----|------|-------|
| Linux | `ss` (modern) | Pre-installed (iproute2) |
| Linux | `netstat` (legacy) | Install via net-tools |
| Windows | `netstat` | Pre-installed, different syntax |
| macOS | `netstat` | Pre-installed (BSD version) |

```bash
# Install netstat on Linux (if needed)
sudo apt install net-tools

# ss is pre-installed (part of iproute2)
```
