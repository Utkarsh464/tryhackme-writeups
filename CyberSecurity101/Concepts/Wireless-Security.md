# Wireless Security

## Definition
Wireless security refers to the protection of wireless networks, devices, and communications from unauthorized access, interception, and attacks. It encompasses the security protocols (WEP, WPA, WPA2, WPA3), authentication mechanisms (PSK, Enterprise/802.1X), encryption standards (TKIP, AES-CCMP, AES-GCMP), and best practices for securing Wi-Fi networks against threats like eavesdropping, rogue access points, deauthentication attacks, and KRACK.

## Why It Matters
Wireless networks are ubiquitous — they cover homes, offices, public spaces, airports, and industrial environments. Unlike wired networks, wireless signals propagate through walls and can be intercepted without physical access. This makes wireless security critical for protecting data confidentiality, preventing network intrusion, and maintaining availability. Weak wireless security is one of the easiest attack vectors for penetration testers.

## Where It Appears in the Path
Wireless security is covered in the network security module. It builds on encryption (AES, TKIP), authentication (PSK, 802.1X/EAP), and network fundamentals (SSID, BSSID, channels, frequencies).

## Prerequisites
- Networking fundamentals (MAC addresses, IP addressing)
- Cryptography basics (AES, encryption, authentication)
- Wi-Fi basic concepts (SSID, channel, 2.4/5 GHz)

## Wi-Fi Standards
- **802.11**: Original (1997) — 2 Mbps
- **802.11b**: 11 Mbps, 2.4 GHz (1999)
- **802.11a**: 54 Mbps, 5 GHz (1999)
- **802.11g**: 54 Mbps, 2.4 GHz (2003)
- **802.11n (Wi-Fi 4)**: Up to 600 Mbps, MIMO (2009)
- **802.11ac (Wi-Fi 5)**: Up to 3.5 Gbps, 5 GHz, MU-MIMO (2013)
- **802.11ax (Wi-Fi 6/6E)**: Up to 9.6 Gbps, OFDMA, 2.4/5/6 GHz (2019)
- **802.11be (Wi-Fi 7)**: Up to 46 Gbps, 320 MHz channels (2024)

## Security Protocols

### WEP (Wired Equivalent Privacy) — BROKEN
Introduced in 1997. Uses RC4 stream cipher with 40-bit or 104-bit keys. Weak IV (initialization vector) — only 24 bits, reused after ~5000 packets. Easily cracked in minutes with tools like aircrack-ng. Never use WEP.

### WPA (Wi-Fi Protected Access) — DEPRECATED
Interim solution after WEP was broken. Used TKIP (Temporal Key Integrity Protocol) with RC4. TKIP added per-packet key mixing, message integrity check (MIC), and IV sequencing. Still vulnerable to numerous attacks (Beck-Tews, Ohigashi-Moriai). Deprecated — upgrade to WPA2/WPA3.

### WPA2 (802.11i) — CURRENT STANDARD
Introduced in 2004. Mandated AES-CCMP encryption. Two modes:
- **WPA2-PSK (Pre-Shared Key)**: Single password shared among all clients. Suitable for home/small office.
- **WPA2-Enterprise (802.1X/EAP)**: Centralized authentication via RADIUS server. Each user has unique credentials. Certificate-based. Required for enterprise environments.

**Known Vulnerabilities**: KRACK (Key Reinstallation Attack, 2017) — exploits the 4-way handshake to force nonce reuse and decrypt traffic. Patched in most implementations. Still considered secure with patched clients.

### WPA3 (Wi-Fi 6 compatible) — LATEST STANDARD
Introduced in 2018. Major improvements over WPA2:
- **Simultaneous Authentication of Equals (SAE)**: Replaces PSK pre-shared key exchange with Diffie-Hellman handshake. Resists offline dictionary attacks.
- **192-bit Security Suite**: For Enterprise mode (aligned with CNSA).
- **Protected Management Frames (PMF)**: Mandatory — prevents deauthentication and disassociation attacks.
- **Forward Secrecy**: Past traffic cannot be decrypted even if the password is later compromised.
- **Easy Connect (Wi-Fi DPP)**: QR code-based device onboarding.

**Known Weaknesses**: Dragonblood attacks on early WPA3 implementations (downgrade attacks, side-channel leaks). These targeted specific implementations, not the protocol itself. Patched in later firmware.

## Wi-Fi Authentication

### PSK (Pre-Shared Key)
Single password configured on the access point. All clients use the same password. Simple but scales poorly — changing the password requires reconfiguring all devices.

### Enterprise (802.1X/EAP)
Each user authenticates individually through an authentication server (RADIUS). Supports EAP methods (PEAP, EAP-TLS, EAP-TTLS):
- **EAP-TLS**: Certificate-based on both client and server. Most secure.
- **PEAP**: Tunnel inside TLS — client authenticates via MSCHAPv2 inside encrypted TLS tunnel.
- **EAP-TTLS**: Similar to PEAP but more flexible authentication inside the tunnel.

## Common Attacks

### Deauthentication Attack
Send forged deauth management frames to disconnect clients from the access point. WPA2 does not protect management frames (PMF was optional). Used to capture WPA handshakes for cracking.

### KRACK (Key Reinstallation Attack)
Exploits a vulnerability in the WPA2 4-way handshake to force nonce reuse. Allows decryption of traffic without knowing the password. Patched in 2017. WPA3 is not vulnerable.

### Evil Twin / Rogue Access Point
Attacker sets up a malicious AP with the same SSID as a legitimate network. Victims connect to the evil twin, allowing the attacker to intercept traffic, capture credentials, or serve malicious content.

### WPA/WPA2 PSK Cracking
Capture the 4-way handshake (via deauth attack) and attempt offline brute-force/dictionary cracking. Use aircrack-ng, hashcat, or John the Ripper with tools like aircrack-ng, hcxdumptool.

### WPS PIN Attack
Wi-Fi Protected Setup (WPS) PIN is an 8-digit number. The last digit is a checksum, and the protocol validates the first and second halves separately — only 11,000 attempts needed to brute-force. Tools: Reaver, PixieWPS.

### Beacon Flood / Probe Request Flood
Flood management frames to overwhelm APs or disrupt client connections.

## Defensive Best Practices
- Use WPA3 if available. If not, use WPA2-AES with strong password (12+ random characters).
- Disable WPS.
- Use enterprise authentication with certificates where possible.
- Implement wireless intrusion detection (WIDS) to detect rogue APs.
- Use VPN over public Wi-Fi.
- Disable SSID broadcast (security by obscurity — easily bypassed but reduces casual discovery).
- Keep AP firmware updated.
- Use MAC address filtering (easily bypassed, defense-in-depth only).

## Common Interview Questions
1. **What is the difference between WPA2 and WPA3?** WPA3 uses SAE (Simultaneous Authentication of Equals) replacing PSK, provides forward secrecy, mandates PMF, and uses 192-bit security suite for Enterprise.
2. **What is KRACK and how does it work?** Key Reinstallation Attack — exploits the 4-way handshake to force reuse of nonces in WPA2, allowing decryption. Patched in 2017.
3. **How would you crack a WPA2 password?** Capture the 4-way handshake using deauthentication attack, then use aircrack-ng, hashcat, or John the Ripper with a dictionary/rule-based attack.
4. **What is the difference between WPA2-PSK and WPA2-Enterprise?** PSK: single shared password, no individual authentication. Enterprise: 802.1X/RADIUS with unique credentials per user, significantly more secure.
5. **What is an evil twin attack?** A rogue access point with the same SSID as a legitimate network, tricking users into connecting to it.
6. **How does WPA3 prevent offline dictionary attacks?** SAE uses Diffie-Hellman key exchange — the attacker must interact with the network for each password guess, making offline attacks infeasible.

## Further Reading
- [Wi-Fi Alliance Security](https://www.wi-fi.org/discover-wi-fi/security)
- [KRACK Attack Website](https://www.krackattacks.com/)
- [WPA3 Specification](https://www.wi-fi.org/file/wpa3-specification)
- [Aircrack-ng Documentation](https://www.aircrack-ng.org/documentation.html)
- TryHackMe: Wireless Security room
