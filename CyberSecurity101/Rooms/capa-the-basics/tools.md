# CAPA: The Basics — Tools

## CAPA (Common Analysis Platform for Malware Analysis)
- **Description:** CAPA is an open-source tool developed by Mandiant (Google Cloud) that identifies capabilities in executable files. It analyzes binary files to determine what they are capable of doing — such as installing a keylogger, communicating with a remote server, or modifying system configurations — without requiring the file to be executed.
- **Repository:** https://github.com/mandiant/capa
- **Key Features:**
  - Detects over 800 capabilities organized into hierarchical namespaces
  - Analyzes PE files, ELF files, and .NET assemblies
  - Provides estimated attack vector classification (ransomware, backdoor, etc.)
  - Uses a flexible YAML-based rule system that is user-extensible
  - Outputs results in human-readable text, verbose, or JSON formats
  - Integrates with other Mandiant tools such as FLOSS for string deobfuscation
  - Supports custom rules for detecting organization-specific threats
  - Cross-platform: runs on Linux, Windows, and macOS
- **Use Cases:** Malware triage, SOC analysis, incident response, reverse engineering pipeline, and threat intelligence.

## FLOSS (FireEye Labs Obfuscated String Solver)
- **Description:** FLOSS is a companion tool developed by Mandiant that works alongside CAPA to automatically extract and deobfuscate strings from malware samples. While traditional `strings` output only shows plaintext strings, FLOSS uses advanced static analysis techniques to recover obfuscated, decoded, and stacked strings that malware authors have hidden. It is often used in conjunction with CAPA to provide a more complete picture of a sample's capabilities and indicators.
- **Repository:** https://github.com/mandiant/flare-floss
- **Key Features:** Recovers obfuscated strings using emulation and static analysis, supports PE and ELF formats, integrates with CAPA workflows, cross-platform support.
- **Use Cases:** String extraction from packed samples, IOC identification, malware classification, and supplementing CAPA analysis results.
