# Blue — Concepts

## EternalBlue (MS17-010)
A critical SMB vulnerability discovered by the NSA and leaked by the Shadow Brokers in 2017. Exploits a buffer overflow in the SMBv1 driver (srv2.sys). Allows remote code execution with SYSTEM privileges. Was used in the WannaCry and NotPetya ransomware attacks.

## SMB (Server Message Block)
A network protocol for file sharing, printer sharing, and inter-process communication on Windows networks. SMBv1, the version targeted by EternalBlue, is deprecated due to security concerns.

## CVE-2017-0144
The CVE identifier for the EternalBlue vulnerability. One of several related CVEs (0143-0148) covering different aspects of the SMB vulnerability.

## Buffer Overflow
A vulnerability where a program writes more data to a buffer than it can hold, overwriting adjacent memory. EternalBlue exploits a buffer overflow in the SMB driver to execute arbitrary code.

## NSE (Nmap Scripting Engine)
Used to run the smb-vuln-ms17-010 script for vulnerability identification. Demonstrates how NSE extends Nmap for targeted vulnerability scanning.

## Post-Exploitation Flag Retrieval
The practice of locating and extracting flags in CTF challenges. Flags are typically stored in text files and provide proof of exploitation. Common locations include user desktops, system directories, and application data folders.

## Hashdump
A Meterpreter command that extracts NTLM password hashes from the Windows SAM (Security Account Manager) database. These hashes can be cracked offline with tools like John the Ripper.
