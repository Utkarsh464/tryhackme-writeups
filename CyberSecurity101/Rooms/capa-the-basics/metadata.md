# Room: CAPA: The Basics

## URL
https://tryhackme.com/room/capathebasics

## Description
CAPA (Common Analysis Platform for Malware Analysis) is an open-source tool developed by Mandiant (now part of Google Cloud) that detects capabilities in executable files. Rather than simply scanning for known malware signatures, CAPA analyzes a binary's structure and behavior to identify what it is capable of doing — for example, whether it can install a keylogger, capture screenshots, communicate with a command-and-control server, or modify registry keys. This room introduces learners to CAPA's core functionality, including how to run it against PE (Portable Executable) files, interpret its output, and understand the rule system that underpins its detection engine. Learners will practice analyzing real-world malware samples and benign executables to differentiate between suspicious and legitimate capabilities. The room also covers how CAPA integrates with other analysis tools and how to write custom CAPA rules for detecting specific behaviors. By the end of this room, learners will be comfortable using CAPA as a triage tool to quickly assess unknown binaries and prioritize them for deeper analysis.

## Difficulty
Easy

## Time
~1 hour

## Tier
Premium

## Objectives
- Install and configure CAPA on a Linux or Windows analysis environment
- Run CAPA against PE files to extract capability reports
- Interpret CAPA output including attack vectors, capabilities, and namespaces
- Understand the structure of CAPA rules and how they match binary features
- Differentiate between static analysis indicators and behavioral capabilities
- Use CAPA as a triage tool for prioritizing malware samples

## Tools
- CAPA (Mandiant/Google Cloud)
- Python 3 (for running CAPA)
- PE file samples (benign and malicious)

## Concepts
- Static malware analysis
- PE file structure (sections, imports, exports)
- Capability-based malware classification
- YARA-like rule matching
- Attack vectors in malware analysis
- Triage methodology for unknown binaries
