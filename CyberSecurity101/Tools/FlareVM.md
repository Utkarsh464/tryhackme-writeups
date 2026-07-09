# FlareVM

## Purpose
FlareVM (FireEye Labs Advanced Reverse Engineering Virtual Machine) is a Windows-based security distribution maintained by Mandiant (FireEye/Google Cloud). It transforms a standard Windows installation into a fully equipped malware analysis and reverse engineering environment. FlareVM includes hundreds of pre-configured tools for static analysis, dynamic analysis, debugging, memory forensics, network analysis, and exploit development. It is the Windows counterpart to REMnux, forming a complete cross-platform malware analysis lab.

## Installation
```bash
# Requirements:
# - Windows 10/11 (Pro/Enterprise recommended)
# - 4GB+ RAM (8GB recommended)
# - 60GB+ free disk space
# - Virtual machine snapshot before installation

# Download and run the installer
# Open PowerShell as Administrator
# Install Chocolatey first (if not already installed)
Set-ExecutionPolicy Bypass -Scope Process -Force
iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

# Download and run FlareVM installer
wget https://raw.githubusercontent.com/mandiant/flare-vm/main/install.ps1 -OutFile install.ps1
Unblock-File .\install.ps1

# Optional: Edit the configuration file to customize tool selection
# .\config.xml

# Start installation (takes 1-3 hours)
.\install.ps1
```

## Key Tools Included
- **Disassembly/Debugging**: IDA Pro (Freeware), x64dbg, OllyDbg, Ghidra, radare2, dnSpy, ILSpy
- **Static Analysis**: Detect It Easy (DIE), PEStudio, Exeinfo PE, CFF Explorer, Resource Hacker, LordPE, PEview
- **Dynamic Analysis**: Process Monitor, Process Explorer, ProcDOT, API Monitor, Regshot, TCPView, Wireshark
- **Memory Forensics**: Volatility 2, Volatility 3, Rekall, WinDbg
- **Network Tools**: Wireshark, Fiddler, Python scripts, Netcat, Nmap
- **Scripting**: Python 3, PowerShell, Windows Subsystem for Linux (WSL)
- **Obfuscation**: XORSearch, NoMoreXOR, Balbuzard, RolfRoll, FLOSS
- **Document Analysis**: olevba, oledump, PDF tools, OfficeMalScanner
- **Shellcode**: SCdbg, blobsad, shellcode_encoder
- **Persistence**: Process Hacker, Autoruns, RegJump
- **Utilities**: HxD (hex editor), Strings, Sysinternals Suite, HashMyFiles

## Basic Usage
After installation, tools are accessible from:
- **Start Menu** - Organized by category
- **Desktop Shortcuts** - Key applications
- **Context Menu** - Right-click integration for hash calculation, hex viewing
- **Command Line** - Most tools available via PATH

```powershell
# Launch debugger
x64dbg C:\samples\malware.exe

# Analyze with DIE
die.exe C:\samples\malware.exe

# Extract obfuscated strings
floss C:\samples\malware.exe

# Launch Process Monitor for dynamic analysis
procmon.exe
```

## Typical Workflow
1. Create a snapshot of the clean FlareVM environment
2. Transfer malware sample to the analysis VM (via shared folder or isolated network)
3. Perform static analysis: check file type, hash, strings, packer detection
4. Analyze with CAPA or FLOSS for obfuscated indicators
5. Open in disassembler (Ghidra/IDA) for code-level analysis
6. Take a system snapshot (Regshot) for before/after comparison
7. Execute sample in a debugger (x64dbg) or with API monitoring
8. Analyze dynamic behavior: registry changes, file creation, network connections
9. Extract IOCs and write analysis report
10. Revert to clean snapshot for next sample

## Advantages
- Comprehensive collection of Windows reverse engineering tools in one place
- All tools are pre-configured and tested for compatibility (no dependency conflicts)
- Integration with Windows tooling (Sysinternals, PowerShell, WSL)
- Automated installation script with customizable tool selection
- Regular updates with new tools and versions
- Strong community support with extensive documentation
- Snapshot-ready architecture for fast analysis iteration
- Complements REMnux for a complete cross-platform analysis environment

## Limitations
- Requires a licensed Windows installation (no standalone ISO)
- Very large download and installation (60GB+, 1-3 hours to install)
- Resource intensive (8GB+ RAM recommended for smooth operation)
- Some tools may trigger Windows Defender (exclusions are configured by installer)
- Windows-specific limitations (file system, permissions)
- Not a primary OS replacement (dedicated analysis VM only)

## Industry Use
FlareVM is the standard Windows environment for reverse engineering and malware analysis. Used by security researchers, incident responders, SOC analysts, and threat intelligence professionals. It is commonly paired with REMnux in a malware analysis lab. Mandiant uses it internally and maintains the toolset actively.

## Official Documentation
- GitHub: https://github.com/mandiant/flare-vm
- Installation Guide: https://github.com/mandiant/flare-vm/blob/main/README.md
- Tool List: https://github.com/mandiant/flare-vm/blob/main/README.md#included-tools
- Blog: https://www.mandiant.com/resources/blog/flare-vm-4
- FAQ: https://github.com/mandiant/flare-vm/wiki/FAQ
