# Digital Forensics Fundamentals

## Room Information
- **URL**: https://tryhackme.com/room/digitalforensicsfundamentals
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

## Description

Digital Forensics Fundamentals introduces the scientific discipline of investigating digital evidence in support of security incidents, criminal investigations, and internal inquiries. Digital forensics involves the identification, preservation, collection, analysis, and presentation of digital evidence in a manner that is legally admissible. This room covers the complete forensic process, from the initial identification of potential evidence sources through the final reporting of findings. Learners begin with core forensic principles: Locard's exchange principle (every contact leaves a trace), the importance of maintaining chain of custody (documenting every person who handled evidence), and the order of volatility (collecting the most volatile evidence first). The room then explores forensic acquisition techniques. Disk forensics involves creating bit-for-bit copies (forensic images) of storage devices using tools like dd, FTK Imager, and Guymager. Memory forensics involves capturing RAM contents for analysis of running processes, network connections, and encryption keys using tools like FTK Imager and DumpIt. Network forensics involves capturing and analyzing network traffic with tools like tcpdump and Wireshark. Analysis techniques covered include: file system forensics (understanding NTFS, FAT32, ext4 structures; analyzing MFT records; recovering deleted files through carving), Windows registry analysis (identifying persistence mechanisms, USB device history, recently accessed files), timeline creation (correlating file system timestamps, event logs, and other artifacts), and keyword searching across acquired evidence. The room also covers legal considerations: the difference between criminal and civil investigations, data privacy regulations, and the qualifications required to serve as an expert witness. Practical exercises include creating a forensic image, analyzing file system artifacts, and recovering deleted information.

## Objectives
- Understand digital forensics principles and chain of custody
- Create forensic images of storage devices
- Analyze file systems for evidence of malicious activity
- Examine Windows registry for forensic artifacts
- Capture and preserve volatile memory
- Apply forensic methodology to security investigations

## Tools
- FTK Imager
- Autopsy (Sleuth Kit)
- dd and dcfldd
- Volatility
- Wireshark

## Concepts
- Order of volatility
- Chain of custody
- Forensic imaging vs file copy
- File system artifacts (MFT, timestamps)
- Windows registry analysis
- Memory forensics
- Data carving and recovery
- Legal admissibility of evidence
