# Commands: OSI Model

## Network Diagnostics

| Command | Description |
|---------|-------------|
| `ping -c 4 google.com` | Test network connectivity (Layer 3 reachability) |
| `traceroute google.com` | Trace the path packets take across a network (Layer 3) |
| `netstat -tulpn` | Show listening ports and associated processes (Layer 4) |
| `ss -tulpn` | Modern alternative to netstat for socket statistics |

## Packet Analysis

| Command | Description |
|---------|-------------|
| `tcpdump -i eth0 -n` | Capture packets on an interface without name resolution |
| `tshark -i eth0` | Capture and analyze packets (CLI Wireshark) |
