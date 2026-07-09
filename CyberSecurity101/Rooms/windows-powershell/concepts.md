# Concepts: Windows PowerShell

## 1. PowerShell
Microsoft's task automation and configuration management framework consisting of a shell environment and scripting language built on the .NET Framework. Unlike traditional text-based shells, PowerShell works with .NET objects, enabling powerful data manipulation and automation capabilities far beyond what cmd.exe or Unix shells can achieve.

## 2. Cmdlets (Command-Lets)
Lightweight PowerShell commands following a Verb-Noun naming convention (e.g., Get-Process, Set-ExecutionPolicy, Invoke-WebRequest). Cmdlets are .NET classes that implement specific operations and return .NET objects. They are the building blocks of PowerShell automation.

## 3. Verb-Noun Naming Convention
The standardized naming pattern for PowerShell cmdlets. Approved verbs (Get, Set, New, Remove, Invoke, Start, Stop, etc.) indicate the action, while the noun indicates the target object type. This convention makes cmdlets self-documenting and discoverable via Get-Command.

## 4. PowerShell Pipeline
The mechanism for passing objects from one cmdlet to another using the pipe character (|). Unlike text-based shells where text output is parsed, PowerShell passes complete .NET objects, preserving their structure and properties. Pipelines enable complex data transformations without intermediate files.

## 5. Objects
In PowerShell, everything is a .NET object with properties (data) and methods (actions). Cmdlets produce objects that can be inspected with Get-Member, filtered with Where-Object, selected with Select-Object, and sorted with Sort-Object. This object-oriented approach is PowerShell's key differentiator.

## 6. PowerShell Providers
Components that make data stores appear like filesystem drives, enabling uniform navigation and management. Built-in providers include the filesystem provider (FileSystem:), registry provider (HKLM:, HKCU:), certificate provider (Cert:), environment variable provider (Env:), and function provider (Function:).

## 7. Execution Policy
A PowerShell security feature that controls the conditions under which PowerShell loads configuration files and runs scripts. Policies include Restricted (no scripts), AllSigned (all scripts must be signed), RemoteSigned (downloaded scripts must be signed), and Unrestricted (all scripts run).

## 8. PowerShell Remoting (WinRM)
A feature that allows running PowerShell commands on remote systems using Windows Remote Management (WinRM). Invoke-Command runs one-off commands, while Enter-PSSession starts interactive sessions. Remoting uses HTTP (5985) or HTTPS (5986) and requires appropriate configuration.

## 9. Modules
Packages that contain PowerShell cmdlets, providers, functions, variables, and other resources. Modules extend PowerShell functionality. Common modules include ActiveDirectory (AD management), NetSecurity (firewall), SmbShare (file sharing), and Pester (testing framework).

## 10. Variables and Data Types
PowerShell variables ($variable) can store any .NET object type. Common data types include strings, integers, arrays (@()), hash tables (@{}), Boolean values, and custom objects (PSCustomObject). Variables can be strongly typed ([int]$number) and have scope modifiers ($global, $script, $local).

## 11. Script Blocks
Blocks of PowerShell code enclosed in curly braces { } that can be stored in variables, passed as parameters, and executed with the call operator (&). Script blocks are fundamental to PowerShell's functional programming capabilities and are used extensively in filtering and processing.

## 12. Error Handling
PowerShell provides try-catch-finally blocks for structured exception handling. The $Error automatic variable contains the error history. ErrorActionPreference controls how errors are handled (Continue, Stop, SilentlyContinue, Inquire). The -ErrorAction parameter overrides the default behavior for individual cmdlets.
