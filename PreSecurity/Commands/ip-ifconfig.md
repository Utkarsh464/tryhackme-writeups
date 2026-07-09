# ip / ifconfig

## Syntax
`ip [options] object command` (Linux)
`ifconfig [interface] [options]` (Linux/macOS)

## Purpose
Display and configure network interfaces, IP addresses, routes, and tunnels.

## Common Parameters (ip)

| Parameter | Description |
|-----------|-------------|
| `ip addr` | Show all interface addresses |
| `ip link` | Show/modify link layer (up/down) |
| `ip route` | Show routing table |
| `ip neigh` | Show ARP cache |

## Common Parameters (ifconfig)

| Parameter | Description |
|-----------|-------------|
| `-a` | Show all interfaces (including down) |
| `up/down` | Enable/disable interface |
| `inet addr` | Display IPv4 address |
| `netmask` | Set subnet mask |

## Examples
```bash
ip addr
ip route show
ifconfig
ifconfig eth0 up
ifconfig eth0 192.168.1.10 netmask 255.255.255.0
```

## Compatibility
Linux (ip and ifconfig) | macOS (ifconfig only)