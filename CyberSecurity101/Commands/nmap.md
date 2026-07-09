# nmap

**Network Mapper** — an open-source tool for network discovery and security auditing.

## Syntax

```
nmap [scan type(s)] [options] {target}
```

## Purpose

Discover hosts and services on a network, identify operating systems, detect open ports, running services, and versions. Essential for reconnaissance in penetration testing.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-sS` | TCP SYN stealth scan (default) |
| `-sT` | TCP connect scan |
| `-sU` | UDP scan |
| `-sV` | Version detection on open ports |
| `-O` | Operating system detection |
| `-A` | Aggressive mode (OS, version, script, traceroute) |
| `-p` | Port range (e.g., `-p 22,80,443` or `-p-` for all) |
| `-T0`–`-T5` | Timing templates (0=paranoid, 5=insane) |
| `-oN/-oX/-oG` | Output to normal/XML/grepable format |
| `-v` | Increase verbosity |
| `-Pn` | Skip host discovery (assume host is up) |
| `--script` | Run NSE scripts (e.g., `--script vuln`) |

## Examples

```bash
# Basic port scan of top 1000 ports
nmap 10.10.10.1

# Scan all ports with service detection
nmap -p- -sV 10.10.10.1

# Aggressive scan with OS detection and default scripts
nmap -A 10.10.10.1

# Scan a subnet for live hosts (ping sweep)
nmap -sn 10.10.10.0/24

# Run vulnerability scripts
nmap --script vuln 10.10.10.1

# Save output to a file
nmap -sS -sV -oN scan.txt 10.10.10.1
```

## Common Mistakes

- Running aggressive scans (`-A`) without permission — illegal in many jurisdictions.
- Assuming all ports are discovered — default scan only covers 1000 ports. Use `-p-` for full coverage.
- Forgetting `-Pn` when the target blocks ICMP — the scan will hang waiting for a host that won't respond.
- Using too fast a timing (`-T5`) on unstable networks — causes packet loss and incomplete results.
- Scanning without understanding the target environment — can trigger IPS/IDS alerts.

## Real-World Usage

- **Red team reconnaissance:** Identify attack surface by enumerating open ports and services.
- **Vulnerability assessment:** Use NSE scripts to detect specific CVEs like EternalBlue (`--script smb-vuln-ms17-010`).
- **Network inventory:** Map all devices on a corporate network for asset management.
- **Firewall auditing:** Determine which ports pass through a firewall using decoy scans and fragmented packets.
- **CTF challenges:** In TryHackMe rooms, nmap is the first tool used to discover attack vectors.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Native install via apt/pacman/yum |
| Windows | Full | Npcap driver required for raw packets |
| macOS | Full | Install via Homebrew |

```bash
# Install on Linux
sudo apt install nmap            # Debian/Ubuntu
sudo yum install nmap            # RHEL/CentOS

# Install on macOS
brew install nmap
```
