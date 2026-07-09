# Nmap: The Basics — Concepts

## Port Scanning
The process of probing a target for open ports. Each open port represents a potential service and attack vector. Nmap supports multiple scan types for different scenarios.

## TCP SYN Scan (Stealth Scan)
Sends a SYN packet and observes the response. SYN-ACK means the port is open; RST means closed. The connection is never fully established, making it less likely to be logged.

## TCP Connect Scan
Completes the full TCP three-way handshake for each port. More likely to be logged but does not require root privileges.

## Service Version Detection
Nmap probes open ports with specific payloads to determine the exact service and version running. Identifies software names, versions, and sometimes additional configuration details.

## OS Fingerprinting
Nmap analyzes subtle differences in TCP/IP stack behavior to infer the operating system of the target. Factors include initial TTL values, window sizes, and TCP option ordering.

## NSE (Nmap Scripting Engine)
A Lua-based scripting engine that extends Nmap's capabilities. Scripts can perform advanced enumeration, vulnerability detection, brute-force attacks, and service interaction.

## Timing Templates
Predefined timing profiles (-T0 through -T5) that control scan speed. Paranoid (-T0) is slowest and least intrusive. Insane (-T5) is fastest but may cause packet loss.
