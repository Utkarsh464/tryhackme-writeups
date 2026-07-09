# Concepts: Windows Fundamentals Part 2

## 1. User Account Control (UAC)
A Windows security feature that prevents unauthorized system changes by prompting for administrator approval or credentials before allowing actions that affect system settings or other user accounts. UAC helps prevent malware from making system-wide changes without user knowledge.

## 2. Local Users and Groups
Windows user accounts and groups that are stored locally on a single system (not in Active Directory). Built-in accounts include Administrator and Guest. Built-in groups include Administrators (full system access), Users (standard user access), Guests (limited access), and Remote Desktop Users (RDP access).

## 3. Windows Security Policies
Configurable rules that govern security behavior on a Windows system. Account policies control password requirements (complexity, length, age) and account lockout thresholds. Local policies include audit policies (tracking events), user rights assignments (privileges), and security options (system-wide settings).

## 4. Windows Registry
A hierarchical database that stores configuration settings for the Windows operating system and installed applications. The registry contains keys (like folders) and values (like files). Root keys include HKEY_CLASSES_ROOT (file associations), HKEY_CURRENT_USER (current user settings), HKEY_LOCAL_MACHINE (system-wide settings), HKEY_USERS (all user profiles), and HKEY_CURRENT_CONFIG (hardware profiles).

## 5. Group Policy
A feature that allows centralized management of operating system settings, application configurations, and security settings for users and computers in an Active Directory environment. Local Group Policy (gpedit.msc) provides similar functionality for individual systems.

## 6. Windows Networking
Windows networking capabilities include TCP/IP configuration (DHCP, static IP), network discovery (finding other devices), file and printer sharing (SMB/CIFS protocol), and network location profiles (Domain, Private, Public). Each profile has different firewall and sharing settings.

## 7. Remote Desktop Protocol (RDP)
A proprietary Microsoft protocol that provides remote graphical access to a Windows computer. RDP allows users to connect to and control a remote Windows machine as if they were sitting in front of it. RDP uses port 3389 and requires appropriate permissions and firewall rules.

## 8. File Sharing (SMB)
Server Message Block (SMB) protocol enables file and printer sharing on Windows networks. Shared folders can be accessed via UNC paths (\\server\share). Permissions are controlled through share permissions and NTFS file permissions, with the most restrictive permission applying.

## 9. User Rights
Privileges assigned to users or groups that determine what actions they can perform on the system. Examples include SeNetworkLogonRight (access computer from network), SeInteractiveLogonRight (log on locally), SeShutdownPrivilege (shut down system), and SeServiceLogonRight (log on as a service).
