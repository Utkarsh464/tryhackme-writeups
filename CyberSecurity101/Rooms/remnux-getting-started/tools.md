# REMnux: Getting Started — Tools

## REMnux Distribution
- **Description:** REMnux is a free Linux distribution for reverse engineering and malware analysis, maintained by Lenny Zeltser. It includes hundreds of preinstalled tools organized by category and is available as a virtual machine, Docker container, or installable package set for Ubuntu.
- **Website:** https://remnux.org/
- **Key Tools Included:**
  - Static analysis: radare2, strings, xxd, pestudio alternatives
  - Document analysis: oletools, pdfid, pdf-parser, Didier Stevens' suite
  - Network analysis: Wireshark, tcpdump, ngrep, ncat
  - Memory forensics: Volatility, bulk_extractor
  - Reverse engineering: x64dbg (via Wine), Ghidra, ILSpy
  - Packer detection: PEiD, Detect It Easy
  - Debugging: edb-debugger, strace, ltrace
- **Use Cases:** Malware analysis, reverse engineering, forensic investigation, suspicious file analysis, and CTF challenges.

## oletools (Didier Stevens Suite)
- **Description:** oletools is a collection of Python tools for analyzing Microsoft OLE2 files (Compound Binary File Format), which are used by Office documents. The suite includes `oleid` for identifying risky indicators, `olevba` for extracting and analyzing VBA macros, `mraptor` for macro risk assessment, `oledump` for examining OLE streams, and `rtfobj` for analyzing embedded objects in RTF files. These tools are essential for analyzing document-based malware delivery.
- **Website:** https://github.com/decalage2/oletools
- **Key Tools:** oleid, olevba, mraptor, oledump, rtfobj, pyxswf
- **Use Cases:** Analyzing malicious Office documents, extracting macro source code, detecting embedded executables, and assessing document risk levels during malware triage.

## radare2
- **Description:** radare2 (r2) is a powerful open-source reverse engineering framework that provides disassembly, debugging, binary analysis, and code patching capabilities. It supports dozens of CPU architectures and file formats, making it suitable for analyzing both PE files and ELF binaries. REMnux includes radare2 preinstalled with helpful plugins and scripts for malware analysis workflows.
- **Website:** https://rada.re/n/
- **Key Features:** Multi-architecture disassembly, hex editor, debugger, emulation via ESIL, scripting in Python and JavaScript, and extensive plugin ecosystem.
