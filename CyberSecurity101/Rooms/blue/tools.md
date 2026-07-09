# Blue — Tools

- **Nmap:** Used for initial reconnaissance to discover open ports and services. The NSE script smb-vuln-ms17-010 confirms the EternalBlue vulnerability.
- **Metasploit Framework (msfconsole):** Provides the EternalBlue exploit module (exploit/windows/smb/ms17_010_eternalblue) and generates the Meterpreter payload.
- **Meterpreter:** The advanced payload that provides post-exploitation capabilities including hash dumping, file system navigation, and command execution.
- **EternalBlue Exploit Module:** A Metasploit module that implements the MS17-010 exploit. Delivers a payload with SYSTEM-level privileges due to the kernel-level nature of the vulnerability.
- **John the Ripper:** Can be used offline to crack the NTLM hashes extracted via hashdump, potentially revealing plaintext passwords.
- **Searchsploit:** Useful for finding additional information and proof-of-concept code for MS17-010.
