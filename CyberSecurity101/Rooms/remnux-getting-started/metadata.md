# Room: REMnux: Getting Started

## URL
https://tryhackme.com/room/remnuxgettingstarted

## Description
REMnux is a specialized Linux distribution designed for reverse engineering and malware analysis. Built on Ubuntu, it comes preconfigured with hundreds of tools for static and dynamic analysis of malicious software, memory forensics, network traffic analysis, and suspicious document examination. This room guides learners through the process of downloading, installing, and navigating REMnux for the first time. Learners will explore the desktop environment, understand how to launch key tools from the command line and GUI menus, and practice common analysis workflows. The room covers static analysis tools for examining PE files (radare2, pestudio alternatives), tools for analyzing suspicious documents (oletools for Office documents, pdfid and pdf-parser for PDFs), network analysis tools (Wireshark, tcpdump, ngrep), and memory analysis tools (Volatility, bulk_extractor). Learners will also work with REMnux's curated malware sample repository to practice hands-on analysis. By the end of this room, learners will be comfortable using REMnux as their primary analysis environment and will understand how its toolset fits into the broader malware analysis lifecycle.

## Difficulty
Easy

## Time
~1 hour

## Tier
Premium

## Objectives
- Download, install, and launch REMnux as a virtual machine or Docker container
- Navigate the REMnux desktop environment and locate key tool categories
- Use static analysis tools to examine PE files and extract metadata
- Analyze suspicious Office documents for malicious macros using oletools
- Examine PDF files for embedded JavaScript and suspicious objects
- Capture and analyze network traffic from a malware sandbox
- Perform basic memory analysis using Volatility

## Tools
- REMnux distribution
- radare2 (r2)
- oletools (oleid, olevba, mraptor)
- pdfid, pdf-parser
- Wireshark, tcpdump
- Volatility
- strings, xxd, file, hexdump

## Concepts
- Malware analysis lifecycle
- Static vs. dynamic analysis
- Sandboxing and isolated analysis environments
- Document-based malware delivery (Office macros, PDF exploits)
- Memory forensics fundamentals
- Network traffic analysis for C2 detection
