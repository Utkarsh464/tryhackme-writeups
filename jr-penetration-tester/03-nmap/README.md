# Module 03: Network Reconnaissance

**Status:** ✅ Completed  
**Rooms:** Passive Reconnaissance, Active Reconnaissance

Techniques for gathering intelligence about target networks. I focused on understanding the trade-off between passive (OSINT, WHOIS, DNS, certificate transparency — undetectable) and active (ping sweeps, traceroute, netcat, curl — noisy but detailed) approaches.

## Rooms

| Room | Topic | Status |
|------|-------|--------|
| Passive Reconnaissance | OSINT, WHOIS, DNS enumeration, certificate transparency | ✅ |
| Active Reconnaissance | Ping sweeps, traceroute, netcat, curl, port probing | ✅ |

## Key Takeaways

- Passive recon leaves no trace on the target — ideal for initial intelligence gathering
- DNS is a goldmine: A, MX, NS, TXT records all reveal infrastructure details
- Certificate transparency logs are a reliable source for discovering subdomains
- Active recon is detectable but necessary for port/service-level enumeration

## Files

- [notes/notes.md](notes/notes.md) — Detailed study notes
- [commands.md](commands.md) — Commands and tools used
- [concepts.md](concepts.md) — Important concepts
- [references.md](references.md) — References and further reading
