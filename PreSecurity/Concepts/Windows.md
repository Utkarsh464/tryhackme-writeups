# Windows

## Definition
Windows is a graphical operating system by Microsoft, based on the **Windows NT** kernel. Key features include **NTFS** (New Technology File System — supports permissions, encryption, compression), **UAC** (User Account Control — privilege elevation prompts), the **Registry** (hierarchical configuration database), and administrative tools like Event Viewer, Task Manager, MMC, and PowerShell.

## Why It Matters
Windows is the dominant desktop OS and widely used in enterprise environments. Understanding Windows internals (processes, services, registry, Active Directory) is crucial for incident response, forensics, privilege escalation, and malware analysis.

## Where It Appears in the Path
- Windows Fundamentals

## Prerequisites
- Basic OS concepts

## Key Points
- NT kernel: handles processes, memory, I/O, security
- NTFS: journaling, permissions (ACE/ACL), EFS encryption, alternate data streams
- UAC runs apps with least privilege; prompts for admin elevation
- Security Identifiers (SIDs) uniquely identify users/groups

## Common Interview Questions
1. What is the Windows Registry?
**Answer:** A hierarchical database storing OS and application configuration settings.
2. What is Active Directory?
**Answer:** A directory service for centralized domain management (users, computers, policies).
3. What is the Local Security Authority Subsystem Service (LSASS)?
**Answer:** A process handling authentication, password changes, and security policies.

## Further Reading
- Microsoft Docs: Windows Architecture
- "Windows Internals" (Russinovich)
- SANS Windows Forensics Posters