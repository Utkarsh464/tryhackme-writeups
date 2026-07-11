# FlareVM: Arsenal of Tools — Concepts

## Dynamic Malware Analysis
Running a malware sample in a controlled environment to observe its behavior in real time. Dynamic analysis captures process creation, file system modifications, registry changes, network connections, and memory manipulation. FlareVM is designed specifically as a dynamic analysis environment.

## Debugging
The process of examining a program's execution by controlling its runtime behavior. Debuggers allow analysts to set breakpoints (pausing execution at specific instructions), step through code line by line, inspect and modify memory and register values, and trace API calls. x64dbg is the primary debugger in FlareVM.

## Process Monitoring
Tracking the activities of a running process including file reads/writes, registry accesses, network connections, thread creation, and DLL loading. Process Monitor (procmon) provides real-time monitoring with extensive filtering and logging capabilities. Understanding what a process does is fundamental to determining malware intent.

## Registry Forensics
The Windows Registry is a hierarchical database that stores system and application configuration data. Malware frequently modifies the registry to achieve persistence (e.g., adding entries to Run keys), store configuration data, or disable security features. RegShot compares registry states before and after execution to identify all changes.

## Packing and Unpacking
Packing is a technique used by malware authors to compress or encrypt the original executable and wrap it in a stub that decompresses or decrypts it in memory. Packers like UPX, Themida, and VMProtect make static analysis more difficult by obfuscating the original code and imports. Detect It Easy identifies packers by analyzing entropy, section names, and other heuristics.

## PE Structure Analysis
The Portable Executable (PE) format is the standard binary format for Windows. Key components include the DOS header (MZ signature), NT headers (file header and optional header), section table (.text for code, .data for initialized data, .rdata for read-only data, .rsrc for resources), import table (DLL functions used), and export table (functions made available). PE-bear and Detect It Easy provide graphical views of PE structure.
