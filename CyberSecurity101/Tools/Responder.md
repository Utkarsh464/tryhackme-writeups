# Responder

## Purpose
Responder is a network poisoning tool used for LLMNR (Link-Local Multicast Name Resolution), NBT-NS (NetBIOS Name Service), and mDNS (Multicast DNS) poisoning attacks. Developed by Laurent Gaffie, Responder listens for name resolution requests on a local network and responds with spoofed answers, redirecting traffic to the attacker's machine. This enables credential harvesting, man-in-the-middle attacks, and SMB relay attacks in Windows network environments. It is a critical tool for internal penetration testing and Active Directory security assessments.

## Installation
```bash
# Kali Linux (pre-installed)
responder -h  # Verify installation

# Clone from GitHub
git clone https://github.com/lgandx/Responder
cd Responder

# Python dependencies
pip install -r requirements.txt

# Docker
docker pull lscr.io/linuxserver/responder

# Manual installation
sudo apt install responder  # On Debian-based systems
```

## Basic Usage
```bash
# Run Responder on the default network interface
sudo responder -I eth0

# Run with specific options
sudo responder -I eth0 -w -r -f

# Analyze mode only (no poisoning)
sudo responder -I eth0 -A

# Start with LDAP and HTTP servers enabled
sudo responder -I eth0 --lm --http
```

## Important Options
- `-I <interface>` - network interface to listen on (e.g., eth0, wlan0)
- `-w` - start WPAD rogue proxy server
- `-r` - answer NetBIOS wredir queries
- `-f` - fingerprint the remote host (operating system version)
- `-A` - analyze mode (listen only, do not poison)
- `-v` - verbose output
- `-F` - force NTLM authentication over basic auth
- `-b` - disable NTLM basic auth (force NTLM)
- `-d` - enable answers for DHCP broadcast requests
- `-s` - answer LLMNR and NBT-NS only if host is in range
- `-u <UPSTREAM>` - upstream proxy for WPAD
- `--lm` - force LM hashing downgrade
- `--basic` - enable basic HTTP authentication
- `--http` - enable HTTP server
- `-e <IP>` - external IP address to redirect to (for multi-homed setups)

## Responder.conf Configuration
The main configuration file (`Responder.conf`) controls which servers are enabled:
```ini
[Responder Core]
SQL = On
SMB = On
HTTP = On
HTTPS = On
LDAP = On
DNS = On
WPAD = On  # Configured separately with -w flag
```

## Typical Workflow
1. Join the target network (physical access or VPN/Layer 2 connectivity)
2. Run Responder in analyze mode first to identify active services: `sudo responder -I eth0 -A`
3. Start full poisoning mode with WPAD: `sudo responder -I eth0 -w -r -f`
4. Wait for clients to make name resolution requests (triggered by user actions, network events, or automated scans)
5. When a victim requests a non-existent hostname, Responder responds with the attacker's IP
6. The victim attempts to authenticate (e.g., via SMB or HTTP), and Responder captures the NTLM hash
7. Hashes are stored in `/usr/share/responder/logs/` in the format `MODULE-IP.txt`
8. Crack captured hashes offline with John the Ripper or Hashcat
9. Alternatively, relay captured NTLM hashes to other systems using Responder's MultiRelay tool

## Advantages
- Automatically captures NTLMv1 and NTLMv2 hashes from network traffic
- No credential cracking needed during the attack phase (capture first, crack later)
- Supports LLMNR, NBT-NS, and mDNS poisoning (covers all Windows name resolution protocols)
- Built-in WPAD server for automatic proxy discovery poisoning
- Fingerprinting capabilities identify target OS versions
- Captures can be relayed to other systems for lateral movement
- Passive analysis mode for reconnaissance without active attacks

## Limitations
- Requires Layer 2 network access (same subnet)
- Modern Windows versions (Windows 10/11) are less vulnerable to LLMNR/NBT-NS poisoning when group policy disables these protocols
- Network monitoring tools can detect the attack (spoofed MAC addresses, unusual traffic patterns)
- Cannot capture credentials for systems using Kerberos (which bypasses NTLM fallback)
- SMB signing prevents relay attacks
- Not effective in segmented networks or with 802.1X authentication
- WPAD attacks require specific browser configurations

## Industry Use
Responder is used by penetration testers during internal network assessments, by red teams for initial access and lateral movement in Active Directory environments, by security auditors testing for LLMNR/NBT-NS vulnerabilities, and by incident responders demonstrating the risks of unsecured name resolution protocols.

## Official Documentation
- GitHub: https://github.com/lgandx/Responder
- Wiki: https://github.com/lgandx/Responder/wiki
- Kali Docs: https://www.kali.org/tools/responder/
- Usage Guide: https://github.com/lgandx/Responder/blob/master/README.md
