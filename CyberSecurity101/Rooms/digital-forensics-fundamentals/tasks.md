# Digital Forensics Fundamentals - Tasks

## Task 1: Introduction to Digital Forensics
- Understand what digital forensics is and its applications
- Differentiate between digital forensics and incident response
- Learn about forensic readiness and preparation

## Task 2: Forensic Principles
- Understand Locard's exchange principle in digital context
- Learn the order of volatility (registers, cache, RAM, disk, network, archives)
- Understand chain of custody requirements
- Learn about evidence integrity verification (hashing)
- Understand the forensic process: identification, preservation, collection, examination, analysis, presentation

## Task 3: Forensic Imaging
- Understand the difference between a file copy and a forensic image
- Learn about write blockers and their importance
- Use dd to create a forensic image
- Use dcfdd or dcfldd for forensic imaging with hashing
- Verify image integrity with SHA-256 or MD5 hashes

## Task 4: File System Forensics
- Understand common file systems (NTFS, FAT, ext4, APFS)
- Learn about Master File Table (MFT) in NTFS
- Analyze file system timestamps (MAC: Modified, Accessed, Changed)
- Understand file carving and recovery of deleted files
- Use Sleuth Kit tools (fls, icat, mmls) for analysis

## Task 5: Windows Registry Analysis
- Understand the Windows registry structure (hives, keys, values)
- Identify persistence mechanisms (Run keys, services, scheduled tasks)
- Analyze USB device history (Enum, MountPoints2)
- Examine recently accessed files and MRU lists
- Use forensic tools to extract and analyze registry data

## Task 6: Memory Forensics
- Understand why memory analysis is important
- Capture volatile memory using FTK Imager or DumpIt
- Use Volatility for memory analysis
- Identify running processes, network connections, and loaded modules
- Extract command-line arguments and process memory dumps

## Task 7: Network Forensics
- Capture network traffic for analysis
- Use Wireshark to examine packet captures
- Identify malicious traffic patterns
- Extract files transferred over the network
- Reconstruct network sessions

## Task 8: Timeline Analysis
- Collect timestamps from multiple sources
- Create a timeline of file system and system activity
- Correlate events to identify attacker actions
- Identify anomalies and deviations from baseline activity

## Task 9: Keyword Searching and Data Filtering
- Perform keyword searches across acquired evidence
- Use grep and strings for text extraction
- Search for specific file types and patterns
- Analyze email and document metadata

## Task 10: Reporting and Legal Considerations
- Write forensic examination reports
- Document findings in a clear, objective manner
- Understand requirements for expert witness testimony
- Learn about data privacy and handling sensitive information

## Task 11: Practical Investigation Exercise
- Acquire and analyze a forensic image
- Identify evidence of malicious activity
- Recover deleted files and extract relevant data
- Create a timeline of events
- Prepare a findings report
