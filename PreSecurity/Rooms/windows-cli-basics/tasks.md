# Tasks: Windows CLI Basics

## Task 1: CMD File Management
**Purpose:** Navigate and manage files using the Command Prompt.

**Skills:** dir, cd, copy, move, del, mkdir, attrib.

**Theory:** CMD provides batch-oriented file management commands. `dir` lists files with attributes. `cd` changes directories. `copy`, `move`, `del` manage files. `mkdir` creates directories. `attrib` views/sets hidden and system attributes. CMD is simpler than PowerShell but still widely used for scripting and quick file operations.

**Commands:** `dir /s`, `cd /d D:\`, `copy C:\a.txt D:\`, `mkdir C:\backup`, `attrib +h file.txt`

---

## Task 2: CMD Network Commands
**Purpose:** Diagnose network connectivity and configuration from CMD.

**Skills:** ipconfig, netstat, ping, tracert, nslookup.

**Theory:** `ipconfig /all` displays full network configuration. `netstat -anb` lists active connections with processes. `ping` tests reachability and latency. `tracert` maps the route to a destination. `nslookup` resolves hostnames to IPs. These commands are essential for network troubleshooting and identifying suspicious connections.

**Commands:** `ipconfig /all`, `netstat -anb`, `ping 8.8.8.8`, `tracert google.com`, `nslookup tryhackme.com`

---

## Task 3: CMD System and Process Management
**Purpose:** Gather system information and manage processes via CMD.

**Skills:** systeminfo, tasklist, taskkill, wmic.

**Theory:** `systeminfo` displays OS details, hardware configuration, hotfixes, and uptime. `tasklist /v` lists processes with verbose details. `taskkill /PID 1234 /F` forces process termination. `wmic` provides WMI access from CMD for system queries.

**Commands:** `systeminfo`, `tasklist /v`, `taskkill /PID 1234 /F`, `wmic useraccount list brief`

---

## Task 4: PowerShell Get-Command and Core Cmdlets
**Purpose:** Learn PowerShell cmdlet discovery and basic usage.

**Skills:** Get-Command, Get-Help, Get-Process, Get-Service.

**Theory:** PowerShell uses verb-noun naming. `Get-Command` discovers available cmdlets. `Get-Help` shows documentation. `Get-Process` lists processes with properties like CPU and memory. `Get-Service` shows service status. These cmdlets return objects (not text), enabling precise property manipulation.

**Commands:** `Get-Command`, `Get-Help Get-Process -Examples`, `Get-Process | Where-Object {$_.CPU -gt 10}`

---

## Task 5: PowerShell Pipeline and Filtering
**Purpose:** Master the PowerShell pipeline for filtering and formatting output.

**Skills:** Pipeline |, Select-Object, Where-Object, Export-CSV.

**Theory:** The PowerShell pipeline passes .NET objects between cmdlets. `Where-Object` filters by property value. `Select-Object` chooses specific properties. `Sort-Object` orders results. The pipeline enables powerful one-liners and replaces lengthy CMD scripts with concise readable pipelines.

**Commands:** `Get-Process | Sort-Object CPU -Descending | Select-Object -First 5`, `Get-Service | Export-CSV services.csv`

---