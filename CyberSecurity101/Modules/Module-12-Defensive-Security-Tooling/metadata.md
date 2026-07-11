# Module 12: Defensive Security Tooling

## Name
Defensive Security Tooling

## Description
This module introduces learners to the essential tools and environments used by defensive security professionals to analyze malware, dissect suspicious files, decode obfuscated data, and investigate security incidents. Defensive security — often referred to as "blue teaming" — relies heavily on a specialized toolset that enables analysts to understand what malicious code is doing, how data is being transformed, and where threats are hiding within a system. In this module, learners will explore four distinct but complementary defensive tools. CyberChef provides a powerful browser-based platform for data transformation, encoding, decoding, encryption, and forensic analysis, making it a must-know utility for any analyst working with raw data or logs. CAPA is a static analysis tool developed by Mandiant that identifies capabilities within executable files, helping analysts quickly determine what a piece of malware is capable of without running it. REMnux is a lightweight Linux distribution specifically engineered for malware analysis, reverse engineering, and suspicious file investigation; it comes preloaded with hundreds of tools for dissecting malicious documents, analyzing network traffic, and examining memory artifacts. Finally, FlareVM is a Windows-based virtual machine environment created by Mandiant that transforms a standard Windows installation into a fully equipped malware analysis workstation, complete with debuggers, disassemblers, unpackers, and forensic utilities. By the end of this module, learners will be comfortable navigating all four environments and using their core tools to perform basic malware analysis and threat investigation tasks.

## Objectives
- Use CyberChef to encode, decode, encrypt, decrypt, and transform data using its extensive recipe library
- Apply the CAPA tool to identify capabilities and behaviors in unknown executable files
- Navigate the REMnux distribution and use its bundled tools for static and dynamic malware analysis
- Set up and configure FlareVM as a dedicated malware analysis workstation
- Perform basic static analysis of suspicious binaries using command-line and GUI tools
- Understand the role of defensive tooling in a SOC or incident response workflow

## Skills
- Data encoding and decoding using CyberChef recipes
- Static analysis of PE files with CAPA
- Malware analysis workflow on REMnux
- Windows-based malware analysis with FlareVM
- Forensic file examination and string extraction
- Capability identification in unknown binaries

## Technologies
- CyberChef (web-based data transformation)
- CAPA (static capability analyzer)
- REMnux (malware analysis Linux distribution)
- FlareVM (malware analysis Windows environment)
- PE file format
- Obfuscation and encoding techniques

## Tools
- CyberChef
- CAPA
- REMnux tools (radare2, oletools, x64dbg, Volatility)
- FlareVM tools (IDA Free, x64dbg, Process Monitor, Process Explorer, HxD)

## Prerequisites
- Basic understanding of file formats and executable types
- Familiarity with Windows and Linux command-line interfaces
- Completion of Module 10 (Defensive Security) recommended

## Outcomes
Upon completing this module, learners will be able to use CyberChef recipes to decode obfuscated data and encode output for analysis, run CAPA against unknown binaries to extract capability reports, navigate the REMnux environment and use its tools for static file analysis, and set up FlareVM to conduct malware analysis on Windows samples. These practical skills form the foundation for a career in malware analysis, incident response, and digital forensics.
