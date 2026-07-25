# Module 04: Nmap

**Status:** ✅ Completed  
**Rooms:** Nmap Live Host Discovery, Nmap Basic Port Scans, Nmap Advanced Port Scans, Nmap Post Port Scans, Protocols and Servers, Net Sec Challenge

The most in-depth module so far. I went from basic host discovery to advanced scan types (ACK, Window, idle/zombie scans) and NSE scripting. The Protocols and Servers room tied scanning back to real-world service vulnerabilities (Telnet cleartext, SMB EternalBlue, FTP anonymous access).

## Rooms

| Room | Topic | Status |
|------|-------|--------|
| Nmap Live Host Discovery | ARP scans, ICMP, TCP/UDP ping sweeps | ✅ |
| Nmap Basic Port Scans | SYN, Connect, UDP, NULL/FIN/Xmas scans | ✅ |
| Nmap Advanced Port Scans | ACK, Window, Maimon, idle/zombie, spoofed scans | ✅ |
| Nmap Post Port Scans | Service version detection, OS fingerprinting, NSE | ✅ |
| Protocols and Servers | Telnet, HTTP, FTP, SMB, SMTP vulnerabilities | ✅ |
| Net Sec Challenge | Capstone applying all network security skills | ✅ |

## Key Takeaways

- Scan type choice matters: SYN is stealthier, Connect is reliable, UDP is slow but necessary
- NSE scripts automate what would take hours of manual enumeration
- Advanced scans (ACK, Window) help identify firewall rules
- Protocol-level knowledge makes scan results actionable — finding port 21 open is trivial, understanding what anonymous FTP access allows is the real skill

## Files

- [notes/notes.md](notes/notes.md) — Detailed study notes
- [commands.md](commands.md) — Commands and tools used
- [concepts.md](concepts.md) — Important concepts
- [references.md](references.md) — References and further reading
