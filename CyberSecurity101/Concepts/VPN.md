# VPN

## Definition
A Virtual Private Network (VPN) creates an encrypted tunnel between a device (or network) and a remote VPN server, extending a private network across a public network like the Internet. VPNs provide confidentiality (encryption), integrity (tamper detection), and authentication (verifying both ends). They enable remote users to access corporate resources securely and allow organizations to connect geographically separated networks.

## Why It Matters
VPNs are fundamental to enterprise security and remote access. They protect data on untrusted networks (public Wi-Fi, ISP connections), enable secure remote work, connect branch offices, and provide privacy from ISPs and surveillance. In cybersecurity, VPNs are also used by attackers to anonymize traffic, pivot through compromised networks, and exfiltrate data. Understanding VPN protocols, encryption, and configuration is essential for both defense and offense.

## Where It Appears in the Path
VPNs are covered in the network security module. They require understanding of encryption (AES, RSA), tunneling protocols, IPsec, TLS, and authentication methods. VPNs relate to network segmentation, remote access security, and network forensics (encrypted traffic analysis limitations).

## Prerequisites
- Networking fundamentals (routing, IP addressing, ports)
- Cryptography (symmetric/asymmetric encryption, key exchange)
- OSI model (Layer 2 vs Layer 3 tunnels)

## How VPNs Work
1. VPN client initiates a connection to the VPN server.
2. Client and server authenticate (certificates, pre-shared key, username/password).
3. They negotiate encryption keys and parameters.
4. An encrypted tunnel is established.
5. Data is encrypted by the client, transmitted through the tunnel, decrypted by the server, and forwarded to the destination.
6. Return traffic follows the reverse path.

## Tunneling Protocols

### Layer 2 Tunneling Protocol (L2TP/IPsec)
L2TP provides the tunnel (Layer 2), IPsec provides encryption. Common combination because L2TP alone has no encryption. UDP port 1701 for L2TP, plus IPsec ports (UDP 500, UDP 4500 for NAT-T). Supported natively on most OSes. Slower than modern protocols due to double encapsulation.

### IPsec (Internet Protocol Security)
Operates at Layer 3. Can encrypt any IP traffic (not just specific applications). Two modes:
- **Transport Mode**: Encrypts payload but not header (end-to-end between hosts).
- **Tunnel Mode**: Encrypts entire packet including header (most common for VPNs).

IPsec uses IKE (Internet Key Exchange) for key negotiation over UDP 500. Provides strong security but complex configuration.

### OpenVPN
Open-source VPN based on TLS/SSL. Extremely flexible — can run on any port (commonly UDP 1194), can be configured as TUN (Layer 3, routed) or TAP (Layer 2, bridged). Uses OpenSSL for encryption. Highly configurable (cipher selection, authentication methods, compression). Widely supported across platforms.

### WireGuard
Modern, simple, high-performance VPN. Uses state-of-the-art cryptography (Curve25519, ChaCha20, Poly1305, BLAKE2s, HKDF). Kernel-level implementation in Linux. Single UDP port. Static key configuration (no handshake daemon). Much faster and simpler than OpenVPN or IPsec. Gaining widespread adoption.

### SSTP (Secure Socket Tunneling Protocol)
Microsoft proprietary — uses HTTPS (TCP 443). Can traverse NATs and firewalls easily. Primarily Windows client support. Uses SSL/TLS for encryption.

### IKEv2 (Internet Key Exchange v2)
Microsoft and Cisco collaboration. Often paired with IPsec (IKEv2/IPsec). Fast reconnection (good for mobile users switching networks). Native Windows/iOS support. UDP port 500.

## Site-to-Site vs Remote Access

### Site-to-Site VPN
Connects entire networks (branch office to HQ). Both sides have VPN gateways (routers, firewalls). All traffic between networks goes through IPsec tunnels transparently to users.

### Remote Access VPN
Individual users connect to the corporate network. Each user runs VPN client software. Dial-up VPN (on-demand) or always-on VPN.

## Split Tunneling vs Full Tunneling
- **Full Tunneling**: All traffic goes through the VPN. Ensures all traffic is inspected. Higher latency, increased bandwidth load on VPN server.
- **Split Tunneling**: Only corporate traffic goes through VPN. Internet traffic goes directly. Better performance, but risk of data leakage if split tunnel isn't carefully configured.

## VPN Security Considerations
- **Encryption**: Use strong ciphers (AES-256-GCM, ChaCha20-Poly1305).
- **Authentication**: Certificates (mutual TLS) are better than pre-shared keys or passwords.
- **Kill Switch**: If VPN drops, block all non-VPN traffic to prevent data leaks.
- **DNS Leak Prevention**: Ensure DNS queries go through the VPN tunnel.
- **Perfect Forward Secrecy**: Ephemeral key exchange ensures past traffic is secure if long-term key is compromised.
- **Logging Policy**: Commercial VPN providers may log user activity.

## VPN Evasion (Penetration Testing)
- **Protocol Obfuscation**: Wrapping VPN in HTTPS or random padding to avoid DPI detection.
- **Stealth VPNs**: Modify packet characteristics to evade deep packet inspection (randomize TTL, packet sizes, timing).
- **Port Hopping**: Dynamically change ports to avoid firewall blocks.
- **VPN over VPN (Double VPN)**: Route through multiple VPN servers for additional anonymity.

## Common Interview Questions
1. **What is a VPN and how does it work?** Creates an encrypted tunnel between client and server over a public network, providing confidentiality, integrity, and authentication for data in transit.
2. **What is the difference between OpenVPN and WireGuard?** OpenVPN is TLS-based, highly configurable, widely compatible but slower. WireGuard is modern, kernel-level, uses cutting-edge crypto (ChaCha20, Curve25519), simpler, faster.
3. **What is split tunneling?** Routing only specific traffic (corporate network) through the VPN while other traffic goes directly to the Internet. Pros: performance. Cons: security risk of data leakage.
4. **What is the difference between IPsec transport mode and tunnel mode?** Transport mode encrypts payload only (header remains). Tunnel mode encrypts entire packet (new IP header added). Tunnel mode is used for VPNs.
5. **What ports does OpenVPN use by default?** UDP 1194 (can be configured to any port, TCP possible).
6. **How does a VPN protect against man-in-the-middle attacks?** Authentication (certificates verify server identity), encryption (data is unreadable), and integrity checks (tampering is detected).

## Further Reading
- [OpenVPN Community Documentation](https://openvpn.net/community-resources/)
- [WireGuard Documentation](https://www.wireguard.com/)
- [IPsec HOWTO (StrongSwan)](https://docs.strongswan.org/)
- [NIST SP 800-77 — Guide to IPsec VPNs](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-77r1.pdf)
- TryHackMe: VPN and Tunneling room
