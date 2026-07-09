# ipconfig / ifconfig

**IP Configuration** (`ipconfig` on Windows) / **Interface Configuration** (`ifconfig` on Linux/macOS) — utilities for displaying and configuring network interfaces.

## Syntax (Windows)

```
ipconfig [options]
```

## Syntax (Linux/macOS)

```
ifconfig [interface] [options]
```

## Purpose

Display network interface configuration including IP addresses, MAC addresses, subnet masks, and default gateways. Used for basic network troubleshooting and configuration.

## Common Parameters (ipconfig — Windows)

| Parameter | Description |
|-----------|-------------|
| (no option) | Show all interfaces' IPv4/IPv6 configuration |
| `/all` | Show detailed information (MAC, DHCP, DNS, etc.) |
| `/release` | Release DHCP lease |
| `/renew` | Renew DHCP lease |
| `/flushdns` | Clear DNS resolver cache |
| `/displaydns` | Display DNS resolver cache |
| `/registerdns` | Refresh DHCP and re-register DNS |
| `/showclassid` | Display DHCP class ID |
| `/setclassid` | Set DHCP class ID |

## Common Parameters (ifconfig — Linux/macOS)

| Parameter | Description |
|-----------|-------------|
| (no option) | Show all active interfaces |
| `-a` | Show all interfaces (including down) |
| `<interface>` | Show specific interface only (e.g., `eth0`) |
| `<iface> <ip> netmask <mask>` | Set IP address |
| `<iface> up/down` | Bring interface up or down |
| `<iface> hw ether <mac>` | Change MAC address |
| `mtu <size>` | Set MTU size |
| `promisc` | Enable promiscuous mode |

## Examples

### Windows (ipconfig)

```cmd
# Basic interface display
ipconfig

# Detailed info (MAC, DHCP, DNS)
ipconfig /all

# Release and renew DHCP
ipconfig /release
ipconfig /renew

# Flush DNS cache
ipconfig /flushdns

# Show DNS cache
ipconfig /displaydns
```

### Linux/macOS (ifconfig)

```bash
# Show active interfaces
ifconfig

# Show all interfaces including down
ifconfig -a

# Show specific interface
ifconfig eth0

# Assign IP address
sudo ifconfig eth0 10.10.10.5 netmask 255.255.255.0

# Bring interface up/down
sudo ifconfig eth0 down
sudo ifconfig eth0 up

# Change MAC address (spoofing)
sudo ifconfig eth0 hw ether 00:11:22:33:44:55
sudo ifconfig eth0 up

# Enable promiscuous mode
sudo ifconfig eth0 promisc
```

## ifconfig vs ip

On modern Linux, `ifconfig` is deprecated in favor of the `ip` command. `ip` provides more features and consistent output.

| Task | ifconfig | ip command |
|------|----------|------------|
| Show interfaces | `ifconfig -a` | `ip addr show` |
| Set IP | `ifconfig eth0 10.0.0.1/24` | `ip addr add 10.0.0.1/24 dev eth0` |
| Up/down | `ifconfig eth0 up` | `ip link set eth0 up` |
| Show MAC | `ifconfig eth0` | `ip link show eth0` |

## Common Mistakes

- Using `ifconfig` on modern Linux when `ip` is preferred — ifconfig may not be installed by default on minimal systems.
- Forgetting `sudo` for `ifconfig` changes — modifying interface configuration requires root.
- Confusing `ipconfig` (Windows) with `ifconfig` (Linux) — they have different syntax and options.
- Assuming `ifconfig` output is consistent across Unix-like systems — macOS uses BSD ifconfig with different flags.
- Changing the MAC address without bringing the interface down first — must be down before changing the hardware address.
- Not flushing the DNS cache after network changes — stale DNS entries cause inconsistent behavior.

## Real-World Usage

- **Basic network troubleshooting:** Check assigned IP, verify DHCP worked, confirm DNS settings.
- **MAC address spoofing:** Change MAC address for privacy, bypassing MAC filters, or CTF challenges.
- **DHCP debugging:** Release/renew leases to get a new IP address.
- **CTF challenges:** Configure network interfaces, spoof MAC addresses, identify interface configuration.
- **DNS cache management:** Flush DNS after changing DNS servers or during CTF network recon.

## Compatibility

| OS | Command | Notes |
|----|---------|-------|
| Windows | `ipconfig` | Pre-installed |
| Linux | `ifconfig` | Deprecated, use `ip`; install via `net-tools` |
| macOS | `ifconfig` | Pre-installed (BSD version) |

```bash
# Install ifconfig on Linux
sudo apt install net-tools
```
