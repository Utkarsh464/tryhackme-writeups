# Tasks: Windows Basics

## Task 1: Windows NTFS and Permissions
**Purpose:** Understand NTFS file system capabilities and permission model.

**Skills:** Setting NTFS permissions, understanding ACLs and ADS.

**Theory:** NTFS (New Technology File System) supports file permissions via Access Control Lists (ACLs) with standard levels: Full Control, Modify, Read & Execute, Read, and Write. It also supports Alternate Data Streams (ADS) to hide data within files, file compression, and EFS encryption. Proper permission configuration is essential for data security.

**Commands:** `icacls C:\path`, `icacls C:\path /grant User:F`, `dir /r`

---

## Task 2: User Account Control
**Purpose:** Explain how UAC prevents unauthorised system changes.

**Skills:** Understanding UAC prompts, elevation, and admin vs standard user.

**Theory:** UAC prompts when an application requires administrator privileges. A standard user must enter admin credentials; an admin user receives a consent prompt. This reduces the risk of malware making silent system changes. UAC can be configured via registry or group policy, though disabling it is not recommended.

**Commands:** `net user username /add`, `net localgroup Administrators`, `reg query HKLM\SOFTWARE\...\Policies`

---

## Task 3: Task Manager and Event Viewer
**Purpose:** Navigate Windows diagnostic and monitoring tools.

**Skills:** Monitoring processes, performance, viewing security logs.

**Theory:** Task Manager shows running processes, resource utilisation, and startup programs. Event Viewer catalogs system, security, and application logs under Windows Logs (Security, System, Application). Security logs record logon events, privilege use, and policy changes — critical for incident detection and forensics.

**Commands:** `tasklist /v`, `Get-Process`, `Get-EventLog Security -Newest 10`

---

## Task 4: Services and Local Security Policy
**Purpose:** Manage system services and configure security policies.

**Skills:** Starting/stopping services, configuring password and audit policies.

**Theory:** Services.msc controls Windows services (background processes). Disabling unnecessary services reduces attack surface. Local Security Policy (secpol.msc) configures password policies, account lockout policies, audit policies, and user rights assignments. These are foundational to Windows security hardening.

**Commands:** `services.msc`, `secpol.msc`, `net start "Service Name"`, `sc query`

---

## Task 5: Registry Editor
**Purpose:** Understand the Windows Registry structure and its security role.

**Skills:** Navigating hives, editing keys, understanding Registry as attack vector.

**Theory:** The Registry stores system and application configuration in a hierarchical database. Root keys include HKEY_LOCAL_MACHINE (system-wide settings) and HKEY_CURRENT_USER (per-user settings). Registry keys control everything from security policies to application behaviour. Malware often adds persistence via Run keys. Modifying the Registry can break the system, so caution is required.

**Commands:** `regedit`, `reg query HKLM\SOFTWARE\...\Run`

---