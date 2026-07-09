# Room: Blue

- **URL:** https://tryhackme.com/room/blue
- **Description:** A Capture the Flag room that targets the EternalBlue vulnerability (MS17-010), one of the most notorious exploits in cybersecurity history. Learners will enumerate a Windows target using Nmap, identify the SMB vulnerability, exploit it using Metasploit's MS17-010 module, and perform post-exploitation to retrieve flags. The room provides a complete penetration testing experience from reconnaissance to privilege escalation and credential harvesting, all focused on a single vulnerable Windows machine.
- **Difficulty:** Medium
- **Time:** ~2 hours
- **Tier:** Free
- **Objectives:**
  - Perform Nmap reconnaissance to identify open ports and services
  - Identify the EternalBlue (MS17-010) SMB vulnerability
  - Exploit MS17-010 using Metasploit to gain initial access
  - Escalate privileges to NT AUTHORITY\SYSTEM
  - Dump password hashes using Meterpreter
  - Retrieve flags to complete the Capture the Flag challenge
- **Tools:** Nmap, Metasploit Framework, Meterpreter
- **Concepts:** EternalBlue, MS17-010, SMB, CVE-2017-0144, exploit, privilege escalation, hashdump
