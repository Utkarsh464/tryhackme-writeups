# Module 3: Windows & Active Directory Fundamentals - Quick Reference

## Windows Architecture
- **NT Kernel** - Core OS component managing processes, memory, drivers
- **Win32 API** - Primary programming interface for Windows applications
- **Windows Registry** - Hierarchical database storing OS/app configuration (regedit)
- **Hives**: HKCR (classes), HKCU (current user), HKLM (local machine), HKU (users), HKCC (current config)
- **Services** - Background processes managed by Service Control Manager (services.msc)
- **Processes** - System (kernel), User (applications), svchost.exe (hosts multiple services)
- **Tasks** - Scheduled via Task Scheduler (taskschd.msc)

## File System (NTFS)
- **NTFS Features**: Journaling, permissions (ACLs), encryption (EFS), compression, quotas, symbolic links
- **Permissions**: Full Control, Modify, Read & Execute, List Folder Contents, Read, Write
- **Inheritance**: Child objects inherit parent permissions by default
- **Share Permissions**: Applied at network share level, combined with NTFS (most restrictive wins)
- **Alternate Data Streams (ADS)**: `file.txt:hidden_stream` - used to hide data/malware
- **Volume Shadow Copy (VSS)**: Point-in-time backups (restore previous versions)

## Common Windows Directories
- **C:\Windows** - OS files (System32, SysWOW64 for 32-bit on 64-bit)
- **C:\Program Files** - 64-bit applications
- **C:\Program Files (x86)** - 32-bit applications
- **C:\Users** - User profiles (Desktop, Documents, Downloads, AppData)
- **C:\Users\Public** - Shared files
- **C:\Windows\Temp** and **C:\Users\user\AppData\Local\Temp** - Temporary files

## Active Directory (AD) Basics
- **Domain Controller (DC)** - Server running AD DS, authenticates users/computers
- **Forest** - Top-level container, security boundary
- **Tree** - Collection of domains sharing contiguous namespace
- **Domain** - Administrative boundary, replicated among DCs
- **Organizational Unit (OU)** - Container for organizing objects (users, groups, computers)
- **Objects**: Users, Groups, Computers, Printers, Shared Folders
- **Global Catalog (GC)** - Searchable index of all objects in forest

## AD Authentication
- **Kerberos** - Default AD authentication protocol
  - TGT (Ticket-Granting Ticket) - obtained at login
  - TGS (Ticket-Granting Service) - for accessing specific services
  - Uses port 88 (TCP/UDP)
- **NTLM** - Legacy authentication (challenge-response)
  - NTLM hash created from password
  - Pass-the-Hash attacks exploit NTLM
- **LDAP** - Lightweight Directory Access Protocol (port 389/636)
  - Queries AD objects
  - LDAP://domain.com for binding

## AD Security Concepts
- **Domain Admin** - Highest privilege in domain
- **Enterprise Admin** - Highest privilege in forest (root domain)
- **KRBTGT** - Domain account used for Kerberos ticket encryption
- **Golden Ticket** - Forged TGT using KRBTGT hash (persistence)
- **Silver Ticket** - Forged TGS for specific service
- **Kerberoasting** - Request TGS for service account, crack offline
- **AS-REP Roasting** - Target accounts without pre-authentication required
- **DCSync** - Replicate DC data (including password hashes)
- **Pass-the-Hash** - Authenticate using NTLM hash instead of password
- **Pass-the-Ticket** - Use stolen Kerberos tickets for auth

## Windows Networking
- **SMB** - Server Message Block (port 445) - File sharing, named pipes
- **RDP** - Remote Desktop Protocol (port 3389)
- **WinRM** - Windows Remote Management (port 5985/5986)
- **WMI** - Windows Management Instrumentation (RPC-based)
- **NetBIOS** - Legacy name resolution (port 137-139)
- **DNS** - AD heavily depends on DNS (SRV records for DCs)

## Group Policy
- **GPO** - Group Policy Object (settings applied to users/computers)
- **Computer Configuration** - Applied at boot (software install, security settings)
- **User Configuration** - Applied at login (desktop settings, scripts)
- **Processing Order**: Local → Site → Domain → OU (later wins)
- **gpupdate** - Force policy update
- **gpresult** - Show applied policies
- **RSOP** - Resultant Set of Policy (preview or logging mode)
- **Common GPOs**: Password policy, software restriction, drive mapping, startup scripts

## Windows Security Features
- **UAC** - User Account Control (prompt for elevation)
- **BitLocker** - Full disk encryption
- **Windows Defender/Defender for Endpoint** - AV/EDR
- **AppLocker** - Application whitelisting
- **Credential Guard** - Protects LSASS secrets (VBS-based)
- **LSA Protection** - Restricts access to LSASS process
- **Secure Boot** - Verifies boot components are signed
- **Windows Firewall** - Host-based stateful firewall with advanced security

## Useful Windows Commands
- `whoami /all` - Current user and privileges
- `net users /domain` - List domain users
- `net group "Domain Admins" /domain` - List domain admins
- `net localgroup Administrators` - List local admins
- `gpresult /r` - Show applied GPOs
- `dsquery user -name *admin*` - Search AD for users
- `nltest /dclist:domain` - List domain controllers
- `wmic os get Caption` - Get OS version
- `systeminfo` - System information
- `ipconfig /all` - Network configuration
- `nslookup` - DNS lookup
- `netstat -an` - Active connections
- `tasklist /v` - Running processes
- `schtasks /query` - Scheduled tasks
