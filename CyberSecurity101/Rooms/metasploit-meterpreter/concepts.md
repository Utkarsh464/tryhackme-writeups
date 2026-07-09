# Metasploit: Meterpreter — Concepts

## Meterpreter
An advanced Metasploit payload that provides an extensible, stealthy, and feature-rich interface for post-exploitation. Operates entirely in memory using reflective DLL injection.

## Post-Exploitation
The phase of a penetration test that occurs after initial access is gained. Includes privilege escalation, lateral movement, data extraction, and persistence.

## Privilege Escalation
The process of gaining higher-level permissions on a compromised system. Can be vertical (user to administrator to SYSTEM) or horizontal (user to different user with same privilege level).

## Credential Dumping
Extracting stored credentials from a compromised system. Sources include the SAM database (local hashes), LSASS memory (plaintext passwords), NTDS.dit (domain hashes), and browser credential stores.

## Process Migration
Moving the Meterpreter session from one process to another on the target. Improves stability, evades detection, and can elevate privileges.

## Kiwi (Mimikatz)
A post-exploitation tool for extracting credentials from Windows systems. Loaded in Meterpreter via the `load kiwi` command. Can extract plaintext passwords, hashes, PINs, and Kerberos tickets from memory.

## Pivoting
Using a compromised host as a gateway to access otherwise unreachable networks. The attacker routes traffic through the compromised host, effectively extending the attack surface deeper into the target environment.

## Keylogging
Capturing keystrokes entered on the compromised system. Useful for stealing passwords, sensitive communications, and understanding user behavior.
