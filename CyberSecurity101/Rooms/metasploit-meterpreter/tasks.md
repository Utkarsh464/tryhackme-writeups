# Metasploit: Meterpreter — Tasks

## Task 1: Meterpreter Basics
- **Purpose:** Understand the Meterpreter shell and its capabilities.
- **Skills:** Session interaction, basic Meterpreter commands.
- **Commands:** `getuid`, `sysinfo`, `help`, `getpid`, `ps`
- **Theory:** Meterpreter is an advanced, extensible payload that operates in-memory using DLL injection. It provides a rich set of built-in commands for post-exploitation. Commands are channeled over encrypted connections. The `help` command lists all available Meterpreter commands organized by category.

## Task 2: Privilege Escalation
- **Purpose:** Elevate privileges to gain administrator or SYSTEM access.
- **Skills:** UAC bypass, getsystem, local exploit suggester.
- **Commands:** `getsystem`, `run post/windows/escalate/getsystem`, `run post/multi/recon/local_exploit_suggester`
- **Theory:** `getsystem` attempts multiple privilege escalation techniques including service abuse, named pipe impersonation, and token duplication. The local exploit suggester module analyzes the target and recommends privilege escalation exploits. UAC bypass may be needed on Windows Vista and later.

## Task 3: Credential Dumping
- **Purpose:** Extract password hashes and plaintext credentials from the compromised system.
- **Skills:** Hashdump, kiwi module usage.
- **Commands:** `hashdump`, `load kiwi`, `creds_all`, `lsa_dump_sam`, `wifi_list`
- **Theory:** The `hashdump` command extracts NTLM hashes from the SAM database. Kiwi (a Meterpreter version of Mimikatz) can extract plaintext passwords from LSASS memory, Kerberos tickets, and other credential stores. These credentials can be used for lateral movement or passed to John the Ripper for cracking.

## Task 4: Process Migration
- **Purpose:** Move the Meterpreter session to a more stable or privileged process.
- **Skills:** Process listing, migration target selection.
- **Commands:** `ps`, `migrate <PID>`, `steal_token <PID>`
- **Theory:** Migrating to a different process (e.g., explorer.exe or lsass.exe) improves stability and stealth. If the exploited service crashes, the Meterpreter session survives in another process. Process migration may also elevate privileges if the target process has higher privileges.

## Task 5: Pivoting
- **Purpose:** Use the compromised host as a pivot point to reach internal networks.
- **Skills:** Route addition, port forwarding.
- **Commands:** `run autoroute -s 192.168.2.0/24`, `portfwd add -l 3389 -p 3389 -r 192.168.2.10`
- **Theory:** Pivoting allows the attacker to route traffic through the compromised host to reach otherwise inaccessible internal networks. autoroute adds routes to the Metasploit routing table. portfwd forwards a local port to a remote host through the compromised host, enabling tools on the attacker's machine to interact with internal services.
