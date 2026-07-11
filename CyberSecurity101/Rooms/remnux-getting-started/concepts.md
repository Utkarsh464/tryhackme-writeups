# REMnux: Getting Started — Concepts

## Malware Analysis Lifecycle
A structured process for examining malicious software. The lifecycle typically includes: sample acquisition, static analysis (examining the file without executing it), dynamic analysis (running the sample in a controlled environment), code analysis (reverse engineering the binary), and reporting. REMnux provides tools for each phase.

## Static vs. Dynamic Analysis
Static analysis examines the binary without executing it, focusing on file structure, embedded strings, imported functions, and metadata. Dynamic analysis executes the sample in a sandboxed environment to observe its runtime behavior, network traffic, file system changes, and process interactions. REMnux supports both approaches.

## Sandboxing
An isolated environment used to execute potentially malicious software safely. Sandboxes restrict the malware's ability to affect the host system or network. REMnux itself can serve as a sandbox when run as a VM with network restrictions, though dedicated sandbox tools like Cuckoo provide more automated analysis.

## OLE and Macros
Object Linking and Embedding (OLE) is a technology used by Microsoft Office documents to embed objects, including VBA macros. Malicious actors frequently weaponize Office documents by embedding macros that execute when the document is opened. Tools like olevba extract and analyze macro code to identify malicious behavior such as process injection, download-and-execute routines, and obfuscation.

## PDF Structure
PDF files consist of a header, body (containing objects such as pages, fonts, images, and JavaScript), cross-reference table, and trailer. Malicious PDFs often exploit JavaScript actions, launch actions, or embedded files to deliver malware. pdfid and pdf-parser help analysts examine PDF internals.

## Memory Forensics
The analysis of computer memory (RAM) dumps to extract evidence of malicious activity. Memory forensics can reveal running processes, loaded drivers, network connections, injected code, and encryption keys that are not visible through disk forensics. Volatility is the industry-standard memory forensics framework.
