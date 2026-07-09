# Tasks: Windows PowerShell

## Task 1: Introduction to PowerShell

**Purpose:** Understand what PowerShell is and how it differs from Command Prompt.

**Skills:** PowerShell fundamentals.

**Theory:** PowerShell is an object-oriented shell and scripting language built on .NET. Unlike traditional text-based shells, PowerShell works with .NET objects, enabling powerful data manipulation. Commands are called cmdlets (pronounced command-lets) and follow a Verb-Noun naming convention (Get-Process, Set-ExecutionPolicy). PowerShell can access the filesystem, registry, certificate stores, and WMI.

**Commands:**
- powershell - Launch PowerShell
- Get-Command - List available cmdlets
- Get-Help - Display help for cmdlets
- Get-Verb - List approved verbs
- Get-Member - Display object properties and methods

---

## Task 2: Working with Objects

**Purpose:** Understand how PowerShell manipulates objects.

**Skills:** Object-oriented shell usage.

**Theory:** Everything in PowerShell is an object. Cmdlets produce objects, and the pipeline (|) passes objects between cmdlets. Objects have properties (data) and methods (actions). Get-Member reveals an object's structure. Select-Object picks specific properties, and Where-Object filters objects based on conditions.

**Commands:**
- Get-Member - Examine object members
- Select-Object - Select properties
- Where-Object - Filter objects
- Sort-Object - Sort objects
- Group-Object - Group objects

---

## Task 3: Filesystem and Registry Navigation

**Purpose:** Navigate the filesystem and registry using PowerShell.

**Skills:** Provider navigation.

**Theory:** PowerShell providers allow access to data stores like the filesystem and registry using the same commands. Get-ChildItem lists contents (like dir), Set-Location changes directory (like cd), Get-Content reads files (like type), and Set-Content writes files. The registry is accessed like a filesystem at HKLM:\ and HKCU:\.

**Commands:**
- Get-ChildItem - List items in a location
- Set-Location - Change directory
- Get-Content - Read file content
- Set-Content - Write file content
- Add-Content - Append to file
- Remove-Item - Delete files
- New-Item - Create files or directories
- Copy-Item - Copy items

---

## Task 4: Process and Service Management

**Purpose:** Manage processes and services with PowerShell.

**Skills:** System administration.

**Theory:** PowerShell provides cmdlets for managing system resources. Get-Process and Stop-Process manage running processes. Get-Service, Start-Service, Stop-Service, and Set-Service manage Windows services. These cmdlets can filter, sort, and format output for easy analysis. PowerShell can manage remote systems using -ComputerName parameters or Invoke-Command.

**Commands:**
- Get-Process - List processes
- Stop-Process - Terminate a process
- Get-Service - List services
- Start-Service - Start a service
- Stop-Service - Stop a service
- Restart-Service - Restart a service
- Set-Service - Configure service properties

---

## Task 5: PowerShell Scripting

**Purpose:** Write PowerShell scripts for task automation.

**Skills:** Scripting and automation.

**Theory:** PowerShell scripts are .ps1 files containing cmdlets and scripting constructs. Variables start with $, arrays use @(), hash tables use @{}. Control flow includes if, switch, for, foreach, while, and do-while loops. Functions encapsulate reusable code. Error handling uses try-catch-finally. Execution policies control script execution for security.

**Commands:**
- Get-ExecutionPolicy - View execution policy
- Set-ExecutionPolicy - Set execution policy
- Invoke-Command - Run commands on remote systems
- Export-Csv - Export data to CSV
- Import-Csv - Import data from CSV
- ConvertTo-Json - Convert to JSON
- ConvertFrom-Json - Convert from JSON
