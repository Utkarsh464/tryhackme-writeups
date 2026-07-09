# REMnux

## Purpose
REMnux (Reverse Engineering Malware Linux) is a specialized Linux distribution designed for reverse engineering and analyzing malicious software. Created and maintained by Lenny Zeltser, REMnux includes a comprehensive collection of tools for malware analysis including static analysis utilities, dynamic analysis tools, network forensics utilities, memory analysis tools, and reverse engineering frameworks. It is the most widely used Linux distribution for malware analysis in the cybersecurity community.

## Installation
```bash
# Download the latest REMnux OVA
wget https://REMnux.org/REMnux-8.0.ova

# Import into VirtualBox
VBoxManage import REMnux-8.0.ova

# Or install as a Docker container
docker pull remnux/remnux-distro

# Install tools on top of existing Ubuntu installation
wget https://REMnux.org/remnux-install
chmod +x remnux-install
sudo ./remnux-install

# Update REMnux tools
sudo remnux update
```

## Key Tools Included
- **Static Analysis**: Exeinfo PE, Detect It Easy (DIE), PEStudio (via Wine), DiE, pestudio, file command, strings, xxd, binwalk, radare2, Ghidra
- **Dynamic Analysis**: INetSim (fake internet services), Fakenet-NG, Regshot (via Wine), Process Monitor (via Wine), Wireshark, tcpdump
- **Memory Analysis**: Volatility 3, Volatility 2, Rekall, Linux Memory Extractor (LiME)
- **Network Forensics**: Wireshark, tcpdump, ngrep, NetworkMiner, CapTipper, tshark
- **Obfuscation Analysis**: XORSearch, Balbuzard, NoMoreXOR, XORKeyFinder, base64dump, b64dump
- **Document Analysis**: olevba, oledump, PDFiD, peepdf, Didier Stevens' PDF tools
- **Disassembly**: objdump, ndisasm, radare2, Ghidra, edb-debugger
- **Registry Analysis**: reglookup, python-registry
- **Specialized**: FLOSS (FireEye Labs Obfuscated String Solver), CAPA, YARA, ssdeep

## Basic Usage
REMnux is designed to be used through the command line, with tools available at the terminal:
```bash
# Analyze a suspicious file
file suspicious.exe
strings suspicious.exe
exeinfope suspicious.exe  # GUI tool launched via command

# Extract obfuscated strings
floss suspicious.exe

# Analyze with CAPA
capa suspicious.exe

# Set up fake network services for dynamic analysis
inetsim

# Memory analysis
volatility -f memory.dump imageinfo
```

## Typical Workflow
1. Receive a suspicious file (malware sample, document, script) for analysis
2. Perform initial triage: `file`, `strings`, `exiftool` to identify file type
3. Check file with Detect It Easy for packer detection: `diec sample.exe`
4. Run FLOSS to extract obfuscated strings and decode data
5. Use CAPA to identify high-level malware capabilities
6. Perform static analysis with radare2 or Ghidra for deeper reverse engineering
7. Set up INetSim for safe dynamic analysis with faked network services
8. Execute the sample in a controlled environment while monitoring with Wireshark
9. Analyze captured network traffic for C2 communication
10. Extract IOCs (IPs, domains, hashes, registry keys, file paths)

## Advantages
- Pre-configured environment with hundreds of malware analysis tools
- No tool conflicts or dependency issues (everything is tested together)
- Regular updates with latest analysis tools
- Lightweight and optimized for virtual machine use
- Includes both CLI and GUI tools for different analysis preferences
- InetSim provides safe network simulation for dynamic analysis
- Extensive documentation and tutorials available
- Can be extended with additional tools via apt or manual installation

## Limitations
- Requires virtualization (VMware/VirtualBox) with sufficient RAM (4GB+)
- Not designed for day-to-day use as a primary OS
- Some Windows tools require Wine and may have compatibility issues
- Dynamic analysis requires careful sandbox configuration
- InetSim may not cover all network protocols used by modern malware
- Learning curve for the breadth of available tools

## Industry Use
REMnux is the standard malware analysis platform used by SOC analysts, incident responders, reverse engineers, and threat intelligence analysts. It is commonly paired with FlareVM (Windows) in a malware analysis lab environment. It is used in training courses, CTF competitions, and professional malware analysis workflows.

## Official Documentation
- Official Site: https://REMnux.org
- Documentation: https://docs.REMnux.org
- Tool List: https://REMnux.org/tools
- Installation Guide: https://REMnux.org/install
- Blog: https://zeltser.com/tag/remnux/
- GitHub: https://github.com/REMnux
