# Concepts: Windows Fundamentals Part 3

## 1. Windows Defender Antivirus
Microsoft's built-in antivirus solution providing real-time protection against malware, spyware, and other threats. It includes cloud-delivered protection for rapid response to new threats, controlled folder access (ransomware protection), and periodic scanning options. It is part of the Microsoft Defender security ecosystem.

## 2. Windows Firewall with Advanced Security
A host-based firewall that filters inbound and outbound traffic based on rules. Rules can be configured by program, port, protocol, IP address, and profile (Domain, Private, Public). Connection security rules use IPsec for authentication and encryption. The firewall provides monitoring and logging capabilities.

## 3. BitLocker Drive Encryption
A full disk encryption feature that protects data at rest by encrypting entire drives. BitLocker uses AES encryption algorithms and can use a Trusted Platform Module (TPM) for secure key storage. BitLocker To Go encrypts removable drives. Recovery keys are critical for data access after hardware changes.

## 4. Event Viewer
A Windows application that displays detailed logs about system, security, and application events. Logs are categorized as Application (program events), Security (login attempts, object access), Setup (installation events), System (driver, service, hardware events), and Forwarded Events (collected from remote systems).

## 5. Windows Event Logging
Windows records events with levels of Information (successful operation), Warning (potential issue), Error (problem occurred), Critical (severe failure), and Audit Success/Failure (security-relevant events). Events include Event ID, source, timestamp, category, and detailed description.

## 6. Microsoft Management Console (MMC)
A framework for hosting administrative tools called snap-ins. MMC provides a consistent interface for managing various Windows components. Administrators create custom consoles with specific snap-ins for their tasks. Common snap-ins include Device Manager, Services, Event Viewer, and Group Policy Editor.

## 7. PowerShell
Microsoft's task automation and configuration management framework, consisting of a command-line shell and scripting language built on .NET. PowerShell uses cmdlets (verb-noun commands) and works with .NET objects rather than text, enabling powerful automation and data manipulation capabilities.

## 8. Windows Update
Microsoft's service for distributing security patches, feature updates, and driver updates to Windows systems. Windows Update can be configured for automatic or manual updates. Critical updates address security vulnerabilities and are released on Patch Tuesday (second Tuesday of each month) or as out-of-band emergency patches.

## 9. Patch Management
The process of identifying, acquiring, testing, and installing patches to fix vulnerabilities and improve software functionality. Effective patch management reduces security risk by ensuring systems are protected against known vulnerabilities in a timely manner.

## 10. Windows Security Center
A centralized interface for managing Windows security features including antivirus, firewall, account protection, app and browser control, device security, and device performance and health. It provides a unified view of the system's security status.
