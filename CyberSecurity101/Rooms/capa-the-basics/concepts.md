# CAPA: The Basics — Concepts

## Static Malware Analysis
The process of analyzing a malicious program without executing it. Static analysis examines the file's structure, embedded strings, imported and exported functions, and other metadata to infer its behavior. CAPA is a static analysis tool that identifies capabilities by examining features extracted from the binary.

## PE File Format
Portable Executable (PE) is the file format used by Windows executables, DLLs, and other binary files. Key components include the DOS header, NT headers, section table (.text, .data, .rdata, .rsrc), import table (listing DLL functions the binary calls), and export table (listing functions the binary makes available). CAPA analyzes these structures to identify capabilities.

## Capability-Based Analysis
An approach to malware classification that focuses on what a binary can do (its capabilities) rather than what it looks like (its signature). Capabilities include activities like keylogging, screen capture, file encryption, process injection, network communication, and registry modification. This approach is more robust against obfuscation and polymorphism than signature-based detection.

## CAPA Rules
Rules are the detection logic that CAPA uses to identify capabilities. Rules are written in YAML format and consist of metadata (author, description, references), features (strings, API calls, section names, match conditions), and logical expressions (AND, OR, NOT) that combine features. CAPA ships with hundreds of rules organized by namespace.

## Namespaces
CAPA groups its rules into hierarchical namespaces that organize capabilities by category. Examples include `persistence/registry`, `execution/process-injection`, `defense-evasion/hijack`, `discovery/domain`, `collection/keylog`, and `c2/http`. Namespaces help analysts quickly understand what category of behavior a capability falls under.

## Attack Vectors
CAPA assigns an estimated attack vector label to each analyzed sample based on the combination of capabilities detected. Common attack vectors include Backdoor, Dropper, Downloader, Keylogger, Ransomware, Rootkit, Loader, and Worm. This classification helps analysts triage samples and prioritize their investigation.
