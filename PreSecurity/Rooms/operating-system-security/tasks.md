# Tasks: Operating System Security

## Task 1: User Accounts and Least Privilege
**Purpose:** Manage user accounts and enforce least privilege.

**Skills:** Creating accounts, assigning groups, admin vs standard user.

**Theory:** Least privilege means giving users only the permissions necessary. Admin accounts have full system access; standard users have restricted permissions. Most activity should occur under standard user accounts. Windows uses Local Users and Groups and net commands; Linux uses useradd/usermod/groupadd.

**Commands:** `net user /add`, `net localgroup Administrators`, `useradd -m user`, `usermod -aG sudo user`

---

## Task 2: Authentication and MFA
**Purpose:** Understand authentication factors and implement MFA.

**Skills:** Password, biometric, smart card, TOTP, FIDO2.

**Theory:** Authentication factors: knowledge (password), possession (token), inherence (biometric). MFA combines at least two factors, drastically reducing credential theft risk. Password-only authentication is the weakest; MFA with hardware tokens or TOTP is strongly recommended.

**Commands:** (MFA is typically configured outside the OS, through services like Microsoft Authenticator, Google Auth, or Duo)

---

## Task 3: Password Policies
**Purpose:** Configure strong password policies to resist brute-force attacks.

**Skills:** Complexity requirements, expiration, lockout policy.

**Theory:** Password policies enforce minimum length (12+ chars), complexity (uppercase, lowercase, digit, special), maximum age, and account lockout thresholds. On Windows, configure via secpol.msc. On Linux, use PAM modules (pam_pwquality, pam_faillock).

**Commands:** `secpol.msc` (Windows), `chage -M 90 username` (Linux), `pam-auth-update` (Linux)

---

## Task 4: Patch Management
**Purpose:** Keep the OS updated to protect against known vulnerabilities.

**Skills:** Windows Update, WSUS, apt upgrade, yum update.

**Theory:** Patch management applies vendor-supplied fixes for security vulnerabilities. Windows uses Windows Update or WSUS for enterprise. Linux uses package managers: `apt update && apt upgrade` or `yum update`. Unpatched systems are the most common entry point for attackers.

**Commands:** `sudo apt update && sudo apt upgrade`, `sudo yum update`, `Get-WindowsUpdate`

---

## Task 5: Logging and Firewalls
**What:** Configure system logging and host-based firewalls.

**Skills:** Event Viewer, syslog, auditd, Windows Defender Firewall, iptables.

**Theory:** Logging is essential for detecting and investigating incidents. Windows logs via Event Viewer. Linux uses syslog and auditd for kernel auditing. Firewalls control network traffic. Windows Defender Firewall is managed via GUI or netsh. Linux uses iptables or nftables for packet filtering.

**Commands:** `auditctl -w /etc/passwd -p wa -k passwd-changes`, `sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT`, `netsh advfirewall set allprofiles state on`

---