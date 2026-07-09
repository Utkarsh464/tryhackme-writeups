# ip

**IP** — a command-line utility for viewing and manipulating routing, network devices, interfaces, and tunnels on Linux systems.

## Syntax

```
ip [options] <object> <command>
```

## Purpose

Replacement for the deprecated `ifconfig`, `route`, and `arp` commands. Used to display and configure network interfaces, IP addresses, routing tables, ARP cache, and more.

## Common Objects

| Object | Alias | Description |
|--------|-------|-------------|
| `addr` | `a` | IP addresses on interfaces |
| `link` | `l` | Network interfaces (layer 2) |
| `route` | `r` | Routing table entries |
| `neigh` | `n` | ARP cache (neighbor table) |
| `maddr` | `m` | Multicast addresses |
| `tunnel` | `t` | IP tunnels |
| `netns` | `ns` | Network namespaces |

## Common Commands per Object

### `ip addr`
| Command | Description |
|---------|-------------|
| `ip addr show` | Show all interfaces and IPs |
| `ip addr add <ip>/<mask> dev <iface>` | Add IP address |
| `ip addr del <ip>/<mask> dev <iface>` | Remove IP address |
| `ip addr flush dev <iface>` | Remove all addresses from interface |

### `ip link`
| Command | Description |
|---------|-------------|
| `ip link show` | Show all interfaces (MAC, state, MTU) |
| `ip link set <iface> up/down` | Bring interface up or down |
| `ip link set <iface> mtu <size>` | Change MTU |
| `ip link set <iface> promisc on` | Enable promiscuous mode |

### `ip route`
| Command | Description |
|---------|-------------|
| `ip route show` | Display routing table |
| `ip route add <net>/<mask> via <gateway>` | Add a route |
| `ip route del <net>/<mask>` | Delete a route |
| `ip route get <ip>` | Show route to a specific IP |

## Examples

```bash
# Show all IP addresses
ip addr show

# Show only IPv4 addresses
ip -4 addr show

# Show only a specific interface
ip addr show eth0

# Add an IP address to an interface (like ifconfig alias)
sudo ip addr add 10.10.10.5/24 dev eth0

# Remove an IP address
sudo ip addr del 10.10.10.5/24 dev eth0

# Bring interface down/up
sudo ip link set eth0 down
sudo ip link set eth0 up

# Show routing table
ip route show

# Add default gateway
sudo ip route add default via 10.10.10.1

# Add a specific route
sudo ip route add 192.168.1.0/24 via 10.10.10.254

# Show neighbor (ARP) table
ip neigh show

# Create a network namespace
sudo ip netns add test_ns
sudo ip netns exec test_ns bash

# Show network statistics per interface
ip -s link show eth0
```

## Common Mistakes

- Using deprecated `ifconfig` out of habit — `ip` is the modern tool with more features.
- Forgetting `sudo` for configuration changes — adding/deleting addresses and routes requires root.
- Not specifying the netmask length (`/24`) with `ip addr add` — must use CIDR notation.
- Confusing `ip link set eth0 down` with `ip addr flush eth0` — `down` brings the interface offline; `flush` removes IP addresses while keeping the interface up.
- Using `ip route add default` without a gateway — omitting the `via` parameter fails silently.
- Not understanding that `ip` changes are temporary — they do not persist across reboots unless saved to distribution config files.

## Real-World Usage

- **Network troubleshooting:** Check interface status, IP address assignment, routing.
- **CTF challenges:** Add IP addresses to interfaces, manipulate routing to bypass network restrictions.
- **Container networking:** Manage network namespaces for container isolation.
- **VPN setup:** Add routes to push traffic through VPN tunnels.
- **Penetration testing:** Set up promiscuous mode for packet capture, create network interfaces for VPNs.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (iproute2 package) |
| Windows | N/A | Use `ipconfig`, `route`, `netsh` |
| macOS | N/A | Use `ifconfig`, `networksetup`, `route` |

```bash
# Install on Linux if missing
sudo apt install iproute2
```
