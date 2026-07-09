# Commands: Putting It All Together

## Full Lifecycle Commands

| Command | Description |
|---------|-------------|
| `dig +trace tryhackme.com` | Trace full DNS resolution path |
| `curl -v https://tryhackme.com` | Verbose HTTP request showing headers and TLS handshake |
| `curl -I https://tryhackme.com` | Show only response headers |
| `curl --trace-ascii - https://tryhackme.com` | Full trace of all data sent/received |

## Packet Capture

| Command | Description |
|---------|-------------|
| `sudo tcpdump -i eth0 -n host tryhackme.com` | Capture traffic to/from a specific host |
| `sudo tcpdump -i eth0 'tcp port 443'` | Capture HTTPS traffic (encrypted payloads) |

## Network Diagnostics

| Command | Description |
|---------|-------------|
| `ping -c 4 tryhackme.com` | Test network reachability |
| `traceroute tryhackme.com` | See the network path to a server |
