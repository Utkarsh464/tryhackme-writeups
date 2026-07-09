# CAPA (Common Analysis Platform for Malware)

## Purpose
CAPA is a powerful tool developed by Mandiant (a Google Cloud company) that automatically identifies capabilities in executable files. It analyzes malware samples to detect behaviors such as process injection, keylogging, network communication, persistence mechanisms, anti-analysis techniques, and other runtime characteristics. CAPA combines static analysis with a comprehensive rule set based on IDA Pro, FLOSS, and manual analysis of thousands of malware samples.

## Installation
```bash
# Windows (recommended)
# Download latest release from GitHub
wget https://github.com/mandiant/capa/releases/latest/download/capa-v7.0.0-windows.zip
# Extract and run capa.exe

# Using pip (cross-platform)
pip install flare-capa

# Kali Linux
sudo apt install capa

# Build from source
git clone https://github.com/mandiant/capa.git
cd capa
pip install -e .

# Required dependencies
# capa requires the Vivisect or Ghidra backend
pip install vivisect
# Or set up Ghidra for the Ghidra backend
```

## Basic Usage
```bash
# Analyze a PE file (Windows executable)
capa malware.exe

# Save output to a file
capa malware.exe > analysis.txt

# Verbose output with full rule descriptions
capa -v malware.exe

# Analyze shellcode
capa -f sc32 shellcode.bin

# Use Ghidra backend for deeper analysis
capa -b ghidra malware.exe
```

## Important Options
- `-v` / `--verbose` - detailed output with rule descriptions and rationale
- `-r <directory>` - specify custom rule directory
- `-f <format>` - input format: `pe`, `elf`, `sc32`, `sc64`, `raw32`, `raw64`
- `-b <backend>` - analysis backend: `vivisect` (default), `ghidra`
- `-j` / `--json` - output results in JSON format
- `--color` - enable/disable ANSI color output
- `-t` / `--tag` - filter results by rule tag (e.g., `-t persistence`)
- `-q` / `--quiet` - suppress banner and metadata
- `--signatures` - path to YARA rules for signature matching
- `--overlay` - analyze file overlay data
- `--version` - display version information

## Rule Categories
CAPA organizes capabilities into MITRE ATT&CK-aligned categories:
- **Persistence** - Registry Run keys, scheduled tasks, service installation
- **Defense Evasion** - Process injection, API hooking, code obfuscation, anti-debug
- **Credential Access** - Keylogging, credential dumping (LSASS, SAM), password filtering
- **Discovery** - System info gathering, process enumeration, network discovery
- **Collection** - Screen capture, clipboard monitoring, audio recording
- **Command and Control** - Network communication, DNS tunneling, HTTP/S beacons
- **Exfiltration** - Data compression, encryption, FTP/SMTP-based exfil
- **Impact** - File encryption, bootloader overwrite, service disruption

## Typical Workflow
1. Obtain a suspected malware sample (PE/ELF/Shellcode)
2. Run capa with default options: `capa sample.exe -v`
3. Review the capability summary for high-level behavior categories
4. Drill into specific capabilities in the verbose output to understand implementation
5. Cross-reference findings with MITRE ATT&CK techniques
6. Check for anti-analysis features (anti-debug, anti-VM, obfuscation)
7. Use JSON output for automated processing or integration with other tools
8. If capa is limited (packed samples), try unpacking first or use CAPA with Ghidra

## Advantages
- Fast static analysis (no need to execute malware)
- Comprehensive rule set based on real-world malware analysis
- MITRE ATT&CK alignment for standardized reporting
- Works on PE, ELF, and shellcode formats
- Open-source with active development by Mandiant
- Can be integrated into automated malware analysis pipelines
- Rule language allows community contribution

## Limitations
- Cannot analyze packed or obfuscated executables (requires unpacking first)
- Static analysis only (no dynamic/runtime behavior observation)
- False positives possible when benign software uses similar API patterns
- Limited effectiveness against heavily obfuscated or .NET malware
- Requires understanding of malware analysis concepts to interpret results
- Ghidra backend is significantly slower but more accurate

## Industry Use
CAPA is used by SOC analysts for triaging malware samples, by incident responders for understanding tool capabilities, by malware researchers for initial sample classification, and by threat intelligence teams for extracting IOCs and TTPs. It is a standard component of many malware analysis workflows.

## Official Documentation
- GitHub: https://github.com/mandiant/capa
- Rules: https://github.com/mandiant/capa-rules
- Documentation: https://mandiant.github.io/capa/
- Blog: https://www.mandiant.com/resources/blog/capa-automated-malware-capability-identification
- CAPA Explorer GUI: https://github.com/mandiant/capa-explorer
