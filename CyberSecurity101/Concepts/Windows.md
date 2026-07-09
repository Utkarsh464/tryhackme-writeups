# Windows

## Definition
Microsoft Windows is a family of GUI-based operating systems widely used in corporate environments, personal computing, and enterprise servers. Modern Windows versions (10, 11, Server 2022) are built on the Windows NT architecture, featuring a hybrid kernel, hardware abstraction layer (HAL), and the Win32/Win64 API surface.

## Why It Matters
Windows dominates the enterprise desktop (over 70% market share) and a significant portion of servers. Most corporate networks run Active Directory on Windows Server, making Windows knowledge essential for security professionals. Understanding Windows internals — processes, services, registry, event logging, memory management — is critical for forensics, malware analysis, and penetration testing in Windows environments.

## Where It Appears in the Path
Windows is covered alongside Linux as a core OS concept. Key areas include Windows security features (UAC, BitLocker, AppLocker), Active Directory integration, PowerShell, and Windows-specific attack vectors like SMB exploitation, pass-the-hash, and privilege escalation techniques.

## Prerequisites
- Basic computer literacy
- Familiarity with file systems and user accounts helpful but not required

## Windows OS Architecture
- **Kernel**: Hybrid kernel managing threads, processes, memory, I/O, and security. Runs in kernel mode (ring 0).
- **HAL (Hardware Abstraction Layer)**: Abstracts hardware differences so the kernel remains portable.
- **Executive**: Implements system services — memory manager, process manager, I/O manager, security reference monitor.
- **Win32/Win64 Subsystem**: Provides the Windows API, GUI (USER/GDI), and console support.
- **User Mode**: Applications, services, and subsystem processes run in user mode (ring 3).

## NTFS (New Technology File System)
NTFS is the primary filesystem for Windows NT-based OSes. Key features include:
- **Journaling**: Logs changes before writing to disk, enabling recovery after crashes.
- **Security**: ACLs (Access Control Lists) for per-file/per-directory permissions.
- **Alternate Data Streams (ADS)**: Multiple data streams in one file (often used by malware to hide data).
- **Encryption (EFS)**: Transparent file-level encryption.
- **Compression**: Transparent file compression.
- **$MFT (Master File Table)**: Central catalog of all file metadata.
- **Timestamps**: $STANDARD_INFORMATION (modifiable) and $FILE_NAME (more reliable for forensics).

## UAC (User Account Control)
UAC is a security feature introduced in Windows Vista that runs all users as standard users by default. Administrative tasks trigger a consent prompt (Secure Desktop). This prevents unauthorized system changes and limits malware from gaining full privileges. UAC can be bypassed using techniques like DLL hijacking or registry modification, making it an important attack surface.

## Windows Registry
The Registry is a hierarchical database storing OS and application configuration. Hives include:
- **HKEY_LOCAL_MACHINE (HKLM)**: System-wide settings
- **HKEY_CURRENT_USER (HKCU)**: Current user settings
- **HKEY_CLASSES_ROOT (HKCR)**: File associations and COM object registration
- **HKEY_USERS (HKU)**: All user profiles
- **HKEY_CURRENT_CONFIG (HKCC)**: Hardware profile

Forensic analysis of Registry keys reveals installed software, user activity, USB device history, MRU lists, and network configuration.

## Event Viewer
Windows Event Log records system, security, and application events. Logs are stored in .evtx files. Key log categories:
- **Application**: Application-level events (errors, warnings, info)
- **Security**: Login attempts, privilege use, object access (audit success/failure)
- **System**: Driver failures, service starts/stops, hardware errors
- **PowerShell**: PowerShell script block logging (Event ID 4104)
- **Sysmon**: System Monitor (third-party but widely used) provides detailed process creation, network connection, and file change logging

Event IDs are critical for detection: 4624 (successful logon), 4625 (failed logon), 4688 (process creation), 7045 (service installation).

## Task Manager
Task Manager provides real-time visibility into running processes, resource usage, startup programs, services, and network activity. It enables terminating processes, analyzing performance bottlenecks, and launching new tasks. In cybersecurity, Task Manager is the first stop for spotting suspicious processes (high CPU/memory, unknown names).

## Common Interview Questions
1. **What is the Windows Registry and why is it important for forensics?** A hierarchical database storing OS/app configuration. Forensically interesting for user activity, installed software, MRU lists, and persistence mechanisms.
2. **Explain the difference between a process and a thread in Windows.** A process has its own virtual address space, while threads share the process address space and are units of execution.
3. **What are Alternate Data Streams and how are they used in attacks?** ADS allow multiple data streams within one NTFS file. Attackers hide malicious executables or scripts in ADS (e.g., `file.txt:hidden.exe`).
4. **How does Windows handle authentication?** Local: SAM database. Domain: Kerberos (primary) or NTLM (fallback). Credentials are stored as hashes (LM, NTLM, or NTLMv2).
5. **What is the Windows Sysinternals suite?** A collection of advanced system utilities (Process Explorer, Autoruns, PsExec, Handle) for troubleshooting and forensics.
6. **How do you investigate a compromised Windows system?** Isolate the system, collect memory (RAM dump), capture disk image, analyze Event Logs, Registry hives, prefetch files, $MFT, and recent files.

## Further Reading
- [Microsoft Windows Documentation](https://learn.microsoft.com/en-us/windows/)
- Windows Sysinternals Suite
- _Windows Internals_ by Pavel Yosifovich, Mark Russinovich, David Solomon, Alex Ionescu
- SANS Windows Forensics poster
- [Microsoft Security Event Log Reference](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/)
