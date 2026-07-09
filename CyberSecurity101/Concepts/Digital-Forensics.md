# Digital Forensics

## Definition
Digital forensics is the branch of forensic science encompassing the recovery, preservation, analysis, and presentation of digital evidence from electronic devices and storage media. It follows strict legal and procedural guidelines to ensure evidence is admissible in court. Sub-disciplines include computer forensics, mobile forensics, network forensics, memory forensics, and cloud forensics.

## Why It Matters
Digital forensics is essential for investigating cybercrimes, data breaches, insider threats, and policy violations. Organizations rely on forensics to understand how attacks occurred, what data was compromised, and who was responsible. Forensics also supports incident response (identifying root cause), e-discovery (legal proceedings), and regulatory compliance (GDPR breach notification, PCI DSS). A chain of custody error can destroy a case — procedures matter as much as technical skills.

## Where It Appears in the Path
Digital forensics appears in the defensive/blue team modules. It builds on knowledge from OS fundamentals (Windows registry, Linux file systems, NTFS, file system timeline analysis), networking (packet capture analysis), and cryptography (encrypted evidence).

## Prerequisites
- Operating system fundamentals (Windows/Linux filesystems)
- File system concepts (FAT, NTFS, Ext4)
- Basic networking (for network forensics)

## Forensics Methodology (ACPO/ISO 17025)

### 1. Identification
Recognize and document potential sources of evidence: hard drives, SSDs, USB drives, memory chips, cloud storage, network logs, emails, documents, CCTV footage. Determine scope of the investigation.

### 2. Preservation
Create forensically sound copies before analysis. Use write-blockers to prevent modification of original media. Hash the original evidence (SHA-256) to verify integrity. Maintain chain of custody documentation. Power down running systems to preserve memory? Or capture RAM first? Decision depends on situation.

### 3. Acquisition
Create bit-for-bit copies (images) of storage media. Common formats:
- **DD (raw image)**: Bit-for-bit copy. Simple, widely supported. Large file.
- **E01 (EnCase Evidence File)**: Compressed, segmented, with metadata and integrity checks.
- **AFF (Advanced Forensic Format)**: Open format with compression and metadata.
- **Live Acquisition**: Capturing system memory (RAM) and volatile state from a running system.

### 4. Analysis
Examine acquired data using forensic tools:
- **Timeline Analysis**: Build timelines of file creation, modification, access, deletion events.
- **File Carving**: Recover deleted files from unallocated space using signatures (headers/footers).
- **String Search**: Search for keywords, IPs, emails, credit card numbers.
- **Registry Analysis**: Extract user activity, USB device history, MRU lists, network configuration.
- **Email Analysis**: Headers (tracing routes), attachments, artifacts.
- **Browser Forensics**: History, bookmarks, cache, cookies, download records.
- **Memory Analysis**: Extract processes, connections, loaded modules, passwords, encryption keys from RAM dumps.

### 5. Reporting
Document findings in clear, non-technical language suitable for legal proceedings. Include methodology, tools used, evidence examined, findings, and conclusions. Reports must be objective, accurate, and defensible.

## Chain of Custody
A documented chronological history of how evidence was handled. Every person who touched the evidence, when, where, why, and what was done. Cracks in the chain can make evidence inadmissible. Standard elements: exhibit number, description, location found, collector name, date/time, hash values, transfer history.

## Key Forensic Artifacts

### Windows
- **$MFT**: Master File Table — every file's metadata (timestamps, size, name, parent directory)
- **$J/USN Journal**: Update Sequence Number Journal — records all file changes to NTFS volumes
- **Prefetch files**: Track application launch history (evidence of execution)
- **AmCache.hve**: Application compatibility cache — records installed/run executables
- **Registry hives**: NTUSER.DAT (user activity), SAM (local user accounts), SYSTEM (system config)
- **Event Logs**: .evtx files — security, system, application events
- **Recent Files**: Jump lists, shortcuts (LNK files), search history
- **UserAssist**: Registry key tracking GUI program execution

### Linux
- **Syslog/Journald**: System and application logs
- **Auth.log/secure**: Authentication attempts (success/failure)
- **Bash history**: `.bash_history`, `.bashrc`
- **tmp, /var/tmp**: Temporary file storage
- **Scheduled tasks**: Cron jobs, systemd timers
- **/proc filesystem**: Process information (disappears at shutdown)

### Network
- **PCAP files**: Captured network traffic (tcpdump, Wireshark)
- **NetFlow/IPFIX**: Network flow metadata (connections, volumes, protocols)
- **DNS logs**: Queries made by internal hosts
- **Proxy logs**: HTTP/HTTPS access logs
- **DHCP logs**: IP address assignments

## Forensic Tools

### Open Source
- **Autopsy/Sleuth Kit**: GUI/file system analysis
- **Volatility 3**: Memory forensics
- **Plaso (log2timeline)**: Timeline generation
- **Bulk Extractor**: Parallel data extraction
- **strings, foremost, testdisk**: File carving
- **Wireshark**: Network packet analysis

### Commercial
- **EnCase**: Industry standard forensic platform
- **FTK (Forensic Toolkit)**: AccessData's forensic suite
- **X-Ways Forensics**: Advanced hex editor and forensic tool
- **Cellebrite**: Mobile device forensics
- **Magnet AXIOM**: Cross-platform forensic acquisition and analysis

## Common Interview Questions
1. **What is the first step you take when responding to a digital forensics incident?** Preserve evidence — identify the scope, create a forensic image using write-blockers, hash the original, and document everything with chain of custody.
2. **What is the difference between a forensic image and a backup?** A forensic image is a bit-for-bit copy of the entire storage medium, including unallocated space, slack space, and deleted data. A backup only contains active user files.
3. **How do you maintain chain of custody?** Document every person who handles evidence with date, time, purpose. Sign forms. Seal evidence in anti-static bags. Re-verify hashes at each transfer.
4. **What is file carving and when would you use it?** Recovering files from unallocated space using file signatures (headers/footers). Used when the file system is damaged or files have been deleted.
5. **What artifacts would you look for to determine if a program was executed on Windows?** Prefetch files, AmCache.hve, UserAssist registry key, ShimCache (AppCompatCache), RecentApps (SRUM), $MFT timestamps, Event ID 4688 (process creation).
6. **What is the difference between live forensics and dead forensics?** Live: analyzing a running system (captures memory, active processes, network connections). Dead: analyzing an offline disk image (more thorough, no data volatility concerns).

## Further Reading
- _Digital Forensics and Incident Response_ by Gerard Johansen
- _The Art of Memory Forensics_ by Michael Hale Ligh
- [SANS Digital Forensics](https://www.sans.org/digital-forensics-incident-response/)
- [NIST Computer Forensics Tool Testing](https://www.nist.gov/itl/ssd/software-quality-group/computer-forensics-tool-testing-program-cftt)
- [DFIR Training](https://www.dfir.training/) (resources, tools, and community)
- [CFReDS: Computer Forensic Reference Data Sets](https://cfreds.nist.gov/)
