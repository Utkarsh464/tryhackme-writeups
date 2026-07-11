# FlareVM: Arsenal of Tools — Tasks

## Task 1: Introduction to FlareVM
Learn about the FlareVM project, its origins at Mandiant, and its philosophy of providing a comprehensive Windows-based malware analysis environment. Understand the system requirements and the importance of using an isolated VM.

## Task 2: Setting Up the Windows VM
Create a new Windows 10 or Windows 11 virtual machine in your hypervisor. Allocate sufficient resources (4 GB RAM, 2-4 CPU cores, 80 GB disk). Disable Windows Defender and Windows Update to prevent interference with malicious samples.

## Task 3: Installing FlareVM
Download the FlareVM installer PowerShell script from the official GitHub repository. Open PowerShell as Administrator and execute the installation script. The process will install all 200+ tools, configure shortcuts, and set up the environment. This may take 30-60 minutes.

## Task 4: Exploring the FlareVM Desktop
After installation, explore the Desktop and Start Menu. Notice how tools are organized into categories: Debuggers, Disassemblers, Unpackers, Hex Editors, Network Tools, Forensics, and Utilities. Launch several tools to verify they open correctly.

## Task 5: Using x64dbg
Open a simple compiled binary in x64dbg. Set breakpoints at key API calls (e.g., MessageBox, WriteFile). Step through the program execution using Step Into (F7) and Step Over (F8). Inspect the CPU registers and stack window. Examine the memory map.

## Task 6: Process Monitoring with Procmon
Launch Process Monitor and a test binary. Apply filters to show only file system and registry activity from the target process. Observe which files the process creates, reads, or modifies, and which registry keys it accesses. Export the log for analysis.

## Task 7: Analyzing Registry Changes with RegShot
Take a registry snapshot before executing a malware sample. Execute the sample. Take a second snapshot. Use RegShot's compare function to identify all registry keys and values that were added, modified, or deleted. Focus on persistence mechanisms such as Run keys and service entries.

## Task 8: PE Analysis with Detect It Easy
Open a sample executable in Detect It Easy. Examine the entropy graph to identify packed sections. Review the entropy analysis, section table, imports, and exports. Determine if the binary is packed and, if so, what packer was used. Compare your results with PE-bear's analysis.

## Task 9: Dynamic Analysis Workflow
Conduct a complete dynamic analysis of a provided malware sample: launch the sample while monitoring with procmon and Wireshark, take regex snapshots before and after, capture the process tree with procexp, and use x64dbg to inspect the running process after execution.

## Task 10: Debugging .NET Malware
Use dnSpy to open a .NET-based malware sample. Decompile the code and examine classes, methods, and strings. Set breakpoints in the decompiled source code. Step through the execution and observe how the malware behaves at the source-code level.
