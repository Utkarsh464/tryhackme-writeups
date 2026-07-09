# Tasks: Windows Fundamentals Part 3

## Task 1: Windows Defender Antivirus

**Purpose:** Configure and manage Windows Defender Antivirus.

**Skills:** Antivirus configuration, endpoint protection.

**Theory:** Windows Defender Antivirus is Microsoft's built-in antivirus solution providing real-time protection, cloud-delivered protection, and scheduled scans. Configuration is managed through Windows Security Center or PowerShell. Options include exclusion paths, scan types (quick, full, custom), and notification settings.

**Commands:**
- Get-MpPreference - View Defender settings
- Set-MpPreference - Configure Defender
- Start-MpScan - Initiate antivirus scan
- Update-MpSignature - Update virus definitions

---

## Task 2: Windows Firewall with Advanced Security

**Purpose:** Create and manage advanced firewall rules.

**Skills:** Firewall configuration, network security.

**Theory:** Windows Firewall with Advanced Security (wf.msc) provides host-based traffic filtering. Rules control inbound and outbound traffic based on program, port, protocol, IP address, and profile (Domain, Private, Public). Connection security rules use IPsec for authenticated communication. Monitoring features show active connections and rules.

**Commands:**
- wf.msc - Windows Firewall with Advanced Security
- netsh advfirewall - Firewall command-line tool
- Get-NetFirewallRule - View firewall rules

---

## Task 3: BitLocker Drive Encryption

**Purpose:** Understand full disk encryption with BitLocker.

**Skills:** Data protection, encryption management.

**Theory:** BitLocker encrypts entire drives to protect data at rest. It uses AES encryption and requires a Trusted Platform Module (TPM) for key storage. BitLocker To Go encrypts removable drives. Recovery keys are essential in case of system failure or forgotten PIN. Manage-bde is the command-line tool.

**Commands:**
- manage-bde - BitLocker command-line tool
- repair-bde - BitLocker recovery tool

---

## Task 4: Event Viewer and Windows Logs

**Purpose:** Use Event Viewer for system monitoring and security analysis.

**Skills:** Log analysis, incident detection.

**Theory:** Event Viewer (eventvwr.msc) displays Windows logs including Application, Security, Setup, System, and Forwarded Events. Security logs track login attempts, object access, privilege use, and policy changes. Custom views filter events by ID, level, source, and time range. Events have levels: Information, Warning, Error, and Critical.

**Commands:**
- eventvwr.msc - Event Viewer
- Get-WinEvent - PowerShell event query
- wevtutil - Event log management tool

---

## Task 5: PowerShell and Windows Update

**Purpose:** Perform basic PowerShell commands and manage Windows updates.

**Skills:** Command-line administration, patch management.

**Theory:** PowerShell is Microsoft's task automation framework. Basic cmdlets include Get-Command, Get-Help, Get-Process, and Get-Service. PowerShell can manage Windows Update using the PSWindowsUpdate module or the built-in Windows Update settings. Regular patching is critical for security.

**Commands:**
- powershell - Launch PowerShell
- Get-Command - List available commands
- Get-Process - List running processes
- Get-Service - List services
- wuauclt - Windows Update client
