# SMB

## Definition
Server Message Block (SMB) is a network file sharing protocol that provides shared access to files, printers, serial ports, and miscellaneous communications between nodes on a network. Originally developed by IBM, later heavily extended by Microsoft, SMB is the primary protocol for Windows file and printer sharing. Modern implementations include SMBv2/SMBv3 (improved performance and security) and Samba (open-source implementation for Unix-like systems).

## Why It Matters
SMB is everywhere in Windows enterprise environments. File servers, domain controllers, and workstations all use SMB for file sharing, print services, and inter-process communication. In cybersecurity, SMB is a major attack surface — EternalBlue (MS17-010), the exploit behind WannaCry and NotPetya, targeted SMBv1. Understanding SMB is essential for penetration testing (lateral movement, privilege escalation), forensic analysis, and defensive hardening.

## Where It Appears in the Path
SMB is covered in the Windows networking module. It is critical for understanding Active Directory (domain communication uses SMB), Windows exploitation, and network defense. Tools like `smbclient`, `enum4linux`, `smbmap`, and `Impacket` rely on SMB knowledge.

## Prerequisites
- Windows networking fundamentals
- TCP/IP (ports, connections)

## SMB Versions

### SMBv1 (CIFS)
Original protocol from the 1980s. Extremely chatty, insecure, lacks encryption and signing. All major ransomware exploits (WannaCry, NotPetya) used SMBv1. **Should be disabled everywhere.** Disabled by default since Windows 10/Server 2016.

### SMBv2
Introduced in Windows Vista/2008. Reduced commands from over 100 to 19 (less chatty). Compound operations, larger read/write sizes. Still no encryption — signing added but not mandatory.

### SMBv3 (SMB 2.0.2+)
Introduced in Windows 8/2012. Major security improvements:
- **SMB Encryption**: End-to-end encryption (AES-CCM, AES-GCM).
- **Secure Dialect Negotiation**: Prevents downgrade attacks.
- **SMB Direct (RDMA)**: High-performance with Remote Direct Memory Access.
- **SMB Multichannel**: Aggregate bandwidth across multiple NICs.
- **SMB over QUIC**: SMB over HTTPS (Windows Server 2022+).

## Ports
- **TCP 445**: Direct SMB (over NetBIOS-less transport). Modern default.
- **TCP 139**: SMB over NetBIOS (legacy, NetBIOS session service).
- **UDP 137-138**: NetBIOS name service/datagram (legacy discovery).

## SMB Exploitation

### EternalBlue (MS17-010)
Exploits a buffer overflow in SMBv1's handling of crafted packets. Wormable — spreads automatically without interaction. Used by WannaCry, NotPetya, Retefe banking trojan. Patch MS17-010 released March 2017, but unpatched systems remain.

### Other SMB Attacks
- **SMB Relay (NTLM Relay)**: Intercept SMB authentication and relay to another server.
- **Pass-the-Hash**: Use NTLM hash (not the password) to authenticate over SMB.
- **SMB Null Session**: Anonymous access to SMB shares (disabled by default since Windows 2003).
- **SMB Enumeration**: Enumerate users, shares, groups, OS info via SMB (tools: enum4linux, smbclient, rpcclient).
- **SMBGhost (CVE-2020-0796)**: Uninitialized memory in SMBv3.10 compression handler.
- **SMB Traffic Analysis**: Extract files, credentials, and intelligence from SMB traffic with Wireshark.

## Defensive Best Practices
- Disable SMBv1 completely (registry, Group Policy, or Disable-WindowsOptionalFeature)
- Enable SMB signing (prevents relay attacks, but impacts performance)
- Enable SMB encryption (SMBv3 only)
- Block TCP 445/139 at network perimeter (unnecessary for Internet-facing systems)
- Apply security patches promptly
- Use firewall rules to restrict SMB to authorized subnets
- Monitor Event ID 5140 (network share object accessed) and 5145 (detailed file share access)
- Disable guest access in SMB2/3

## Common Interview Questions
1. **What is SMB and why is it important in cybersecurity?** File sharing protocol used by Windows. Critical attack surface due to EternalBlue, pass-the-hash, and SMB relay attacks.
2. **What is the difference between SMBv1 and SMBv2/3?** SMBv1 is legacy, insecure, chatty, responsible for WannaCry. SMBv2 is more efficient. SMBv3 adds encryption and secure negotiation.
3. **What ports does SMB use?** TCP 445 (direct), TCP 139 (NetBIOS over SMB), UDP 137-138 (NetBIOS name/datagram).
4. **How did EternalBlue (MS17-010) work?** Buffer overflow in SMBv1 handling of crafted packets allowing remote code execution. Wormable.
5. **What is SMB signing and why is it important?** Cryptographic signature on SMB packets to prevent relay attacks and tampering. Important defense against NTLM relay.
6. **How would you enumerate SMB for penetration testing?** Use nmap to scan ports 445/139, smbclient to list shares, enum4linux for user/group enumeration, rpcclient for RPC queries, smbmap for share access.

## Further Reading
- [Microsoft SMB Documentation](https://learn.microsoft.com/en-us/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview)
- [MS17-010 EternalBlue Analysis](https://www.rapid7.com/blog/post/2017/05/12/ms17-010-eternalblue-exploit-analysis/)
- [SMB Security Hardening Guide](https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-security-hardening)
- [SANS SMB Attack Overview](https://www.sans.org/blog/understanding-smb/)
- `smbclient`, `smbmap`, `enum4linux`, `crackmapexec` tools
