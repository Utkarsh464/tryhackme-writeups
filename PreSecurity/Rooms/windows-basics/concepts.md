# Concepts: Windows Basics

## 1. Windows NT Architecture
Windows NT is a hybrid kernel with a hardware abstraction layer (HAL), kernel-mode executive, and user-mode subsystems. It separates kernel mode (privileged, full hardware access) from user mode (restricted, application space). This design balances performance with stability and security.

## 2. NTFS File System
NTFS supports large volumes, ACL-based permissions, journaling (via $LogFile), Alternate Data Streams (ADS — hiding data in files), file compression, and EFS encryption. NTFS permissions are the primary access control mechanism on Windows, overriding share-level permissions when accessed locally.

## 3. NTFS Permission Levels
Standard NTFS permissions include Full Control (all rights), Modify (read, write, execute, delete), Read & Execute (read and run executables), Read (view contents), and Write (create/modify files). Permissions propagate from parent to child (inheritance) unless explicitly blocked.

## 4. User Account Control (UAC)
UAC is a Windows security feature that runs applications in standard user mode by default, elevating only when administrator privileges are required. Admin users receive a consent prompt; standard users must provide admin credentials. This prevents unauthorised system modifications by malicious software.

## 5. Event Viewer and Windows Logging
Event Viewer displays logs categorised by type: System (driver/services), Security (login, privilege use), Application (app errors), and Setup (installation). Security logs are critical for detecting brute-force attacks, privilege escalation, and unauthorised access. Audit policies determine what events are recorded.

## 6. Windows Services (services.msc)
Services are long-running background processes that start automatically or on demand. Each service runs under a specific user account (LocalSystem, NetworkService, or custom). Disabling unnecessary services is a key hardening step — fewer services mean a smaller attack surface and fewer privileged entry points.

## 7. Local Security Policy (secpol.msc)
The Local Security Policy editor manages account policies, audit policies, and user rights assignments. These policies are enforced by the Local Security Authority Subsystem (LSASS).

## 8. Windows Registry
The Registry is a hierarchical database storing system and application configuration in hives. The five root keys are HKLM, HKCU, HKCR, HKU, and HKCC. Malware commonly adds persistence via Run and RunOnce keys. The Registry should be backed up before modification, and suspicious entries can indicate compromise.