# Metasploit: Introduction — Concepts

## Metasploit Framework
An open-source penetration testing platform that enables developing, testing, and executing exploit code. Contains thousands of modules covering exploitation, scanning, evasion, and post-exploitation.

## msfconsole
The command-line interface to the Metasploit Framework. Provides a feature-rich environment with tab completion, scripting support, and resource files for automation.

## Exploit Module
Code that takes advantage of a specific vulnerability to gain access to a target system. Exploits target specific software, versions, and platforms.

## Payload Module
Code that runs on a target system after successful exploitation. Can provide a reverse shell, bind shell, Meterpreter session, or execute specific commands.

## Auxiliary Module
Modules that perform actions other than exploitation. Includes scanners, fuzzers, sniffers, and denial-of-service tools.

## Post-Exploitation Module
Modules that run on an already compromised system. Used for privilege escalation, credential dumping, persistence, and information gathering.

## Encoder Module
Transforms payloads to avoid signature-based detection by antivirus and intrusion detection systems. Shikata Ga Nai is a well-known encoder.

## RHOSTS / LHOST
Metasploit variable naming convention. RHOSTS specifies the target host(s). LHOST specifies the local (attacker) IP address for reverse connections.
