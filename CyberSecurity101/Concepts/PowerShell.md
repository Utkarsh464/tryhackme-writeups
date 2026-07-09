# PowerShell

## Definition
PowerShell is Microsoft's task automation and configuration management framework, consisting of a command-line shell and a scripting language built on .NET. Unlike traditional Unix shells (which work with text), PowerShell works with objects — cmdlets produce .NET objects that can be piped, filtered, and manipulated. PowerShell is deeply integrated into Windows administration and management.

## Why It Matters
PowerShell is the primary administration tool for Windows environments. In cybersecurity, it is heavily used by both attackers and defenders: attackers use PowerShell for fileless malware, in-memory execution, reconnaissance, and lateral movement (PowerShell Empire, Cobalt Strike's PowerShell payloads). Defenders use PowerShell for incident response, log analysis, Active Directory management, and automation of security tasks. Understanding PowerShell is essential for detecting malicious PowerShell usage.

## Where It Appears in the Path
PowerShell is introduced in the Windows module. It is prerequisite for Windows exploitation, Active Directory attacks, incident response automation, and understanding execution policies and logging mechanisms (Script Block Logging, Module Logging).

## Prerequisites
- Windows OS basics (files, processes, services)
- Command-line experience (any shell) helpful but not required

## Cmdlets
Cmdlets (pronounced "command-lets") are lightweight .NET classes that perform a specific operation. Follow a verb-noun naming convention:
- `Get-Process`, `Stop-Process`, `Get-Service`, `Restart-Service`, `Set-Item`, `Remove-Item`
- Common verbs: Get, Set, New, Remove, Start, Stop, Enable, Disable, Invoke, Out

Commonly used cmdlets:
- `Get-Command`: List available cmdlets
- `Get-Help`: Built-in documentation (like man pages)
- `Get-Member`: Examine object properties and methods
- `Select-Object`: Select specific properties
- `Where-Object`: Filter objects by criteria
- `ForEach-Object`: Iterate over objects
- `Sort-Object`: Sort objects by property

## The Pipeline
The pipeline (`|`) passes objects (not text!) from one cmdlet to the next. This is fundamentally different from Linux pipes that pass text streams.
```powershell
Get-Process | Where-Object CPU -gt 50 | Sort-Object CPU -Descending | Select-Object Name, CPU, Id
```
This finds all processes consuming over 50% of CPU, sorts, and displays selected properties.

## Scripting
PowerShell scripts use `.ps1` extension. Supports variables (`$var`), arrays, hashtables, loops, conditionals, functions, and error handling. Scripts can call cmdlets, .NET classes, COM objects, and WMI classes.

### Variables
```powershell
$name = "Alice"
$number = 42
$array = @(1, 2, 3)
$hash = @{ Name="Alice"; Age=30 }
```

### Control Flow
```powershell
if ($value -gt 10) { "Greater" } else { "Less or equal" }
foreach ($item in $collection) { $item }
for ($i=0; $i -lt 10; $i++) { $i }
while ($condition) { }
switch ($value) { 1 { "one" } default { "other" } }
```

### Functions
```powershell
function Get-Greeting {
    param([string]$Name)
    "Hello, $Name!"
}
```

## PowerShell Remoting
Remoting is PowerShell's equivalent of SSH. Uses WinRM (Windows Remote Management) on TCP 5985 (HTTP) and 5986 (HTTPS).
```powershell
Enter-PSSession -ComputerName SERVER01   # Interactive session
Invoke-Command -ComputerName SERVER01 -ScriptBlock { Get-Process }  # One-off command
```
Remoting is a common lateral movement technique — attackers use it to execute commands across the network.

## Execution Policy
A safety feature that controls script execution. Policies: Restricted (default on client), AllSigned, RemoteSigned (default on server), Unrestricted, Bypass. Can be bypassed easily:
```powershell
powershell -ExecutionPolicy Bypass -File script.ps1
powershell -EncodedCommand <base64>
```

## PowerShell Security Logging
- **Script Block Logging**: Logs script block content (Event ID 4104). Critical for detecting malicious scripts.
- **Module Logging**: Logs pipeline execution (Event IDs 4103, 4105, 4106).
- **Transcription**: Records all input/output to a file.
- **Protected Event Logging**: Encrypts logged content with a certificate.

## Common Attack Techniques
- **Reflective Loading**: Load .NET assemblies into memory without writing to disk.
- **PowerShell Empire**: Post-exploitation framework using PowerShell.
- **PowerShell in Cobalt Strike**: Beacon executes PowerShell scripts in memory.
- **DLL Injection via PowerShell**: Use Invoke-Win32 or System.Reflection.
- **Constrained Language Mode Bypass**: Techniques to escape CLM by attackers.

## Common Interview Questions
1. **What is PowerShell and how is it different from CMD?** PowerShell is object-based, built on .NET, supports pipelines of objects, advanced scripting, remoting. CMD is text-based, limited.
2. **What is the PowerShell pipeline?** Passes .NET objects from one cmdlet to the next (not text streams). Enables complex filtering and transformation.
3. **Why is PowerShell important for cybersecurity?** Both attackers (fileless malware, lateral movement) and defenders (automation, incident response, log analysis) use it extensively.
4. **What is PowerShell execution policy and how can it be bypassed?** Restricts script execution. Bypassed with `-ExecutionPolicy Bypass`, `-EncodedCommand`, or direct execution of PowerShell code.
5. **What is Script Block Logging?** Logs PowerShell code blocks to the Windows event log (Event ID 4104). Critical for detection but can be disabled or bypassed.
6. **How would you detect malicious PowerShell activity?** Monitor Event IDs 4104 (script block), 4103 (pipeline), look for base64-encoded commands, reflection, download cradle patterns, obfuscation techniques.

## Further Reading
- [Microsoft PowerShell Documentation](https://learn.microsoft.com/en-us/powershell/)
- [PowerShell MVA (Microsoft Virtual Academy) courses](https://learn.microsoft.com/en-us/training/powershell/)
- [PowerShell ♥ the Blue Team](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
- [PowerShell Attack and Defense (FireEye)](https://www.fireeye.com/blog/threat-research/2016/03/powershell_attackan.html)
- _Learn Windows PowerShell in a Month of Lunches_ by Don Jones
