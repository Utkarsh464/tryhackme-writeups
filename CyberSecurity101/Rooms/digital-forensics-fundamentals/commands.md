# Digital Forensics Fundamentals - Commands

## Forensic Imaging

| Command | Description |
|---------|-------------|
| `dd if=/dev/sda of=/evidence/disk.img bs=4M` | Create raw disk image |
| `dd if=/dev/sda of=/evidence/disk.img bs=4M status=progress` | Image with progress indicator |
| `dcfldd if=/dev/sda of=/evidence/disk.img hash=sha256 hashlog=/evidence/hash.txt` | Image with SHA-256 hash |
| `guymager` | Launch Guymager GUI forensic imager |
| `sha256sum /evidence/disk.img` | Verify image integrity |
| `md5sum /evidence/disk.img` | MD5 checksum verification |

## Sleuth Kit Tools

| Command | Description |
|---------|-------------|
| `mmls /evidence/disk.img` | Display partition layout |
| `fls -o 2048 /evidence/disk.img` | List files in partition at offset 2048 |
| `icat -o 2048 /evidence/disk.img 45 > extracted_file` | Extract file with inode 45 |
| `istat -o 2048 /evidence/disk.img 45` | Display inode information |
| `fsstat -o 2048 /evidence/disk.img` | Display file system statistics |
| `blkcat -o 2048 /evidence/disk.img 1000 10` | Display 10 blocks starting at block 1000 |
| `blkls /evidence/disk.img` | List unallocated blocks |
| `tsk_recover -o 2048 /evidence/disk.img /output_dir` | Recover files to output directory |

## Autopsy / sleuthkit

| Command | Description |
|---------|-------------|
| `autopsy /evidence/disk.img` | Launch Autopsy GUI (note: older version) |
| `autopsy --db /cases/case1.db` | Start Autopsy with case database |

## Volatility Memory Analysis

| Command | Description |
|---------|-------------|
| `volatility -f memory.dmp imageinfo` | Identify memory dump profile |
| `volatility -f memory.dmp --profile=Win7SP1x64 pslist` | List running processes |
| `volatility -f memory.dmp --profile=Win7SP1x64 pstree` | List processes as tree |
| `volatility -f memory.dmp --profile=Win7SP1x64 netscan` | List network connections |
| `volatility -f memory.dmp --profile=Win7SP1x64 cmdline` | Extract command-line arguments |
| `volatility -f memory.dmp --profile=Win7SP1x64 cmdscan` | Extract command history |
| `volatility -f memory.dmp --profile=Win7SP1x64 dlllist` | List loaded DLLs per process |
| `volatility -f memory.dmp --profile=Win7SP1x64 malfind` | Find hidden/injected code |
| `volatility -f memory.dmp --profile=Win7SP1x64 dumpfiles --pid=1234 --dump-dir=./` | Dump process memory |

## Network Forensics

| Command | Description |
|---------|-------------|
| `tcpdump -i eth0 -w capture.pcap` | Capture network traffic to file |
| `tcpdump -r capture.pcap` | Read captured traffic |
| `tcpdump -r capture.pcap -X` | Read with hex and ASCII output |
| `tshark -r capture.pcap -Y "http.request"` | Filter HTTP requests in pcap |
| `tshark -r capture.pcap -T fields -e ip.src -e ip.dst -e http.request.uri` | Extract specific fields |

## Keyword Search and Analysis

| Command | Description |
|---------|-------------|
| `strings /evidence/disk.img \| grep -i password` | Search for password strings in image |
| `strings -e l /evidence/disk.img \| grep -i admin` | Search for Unicode strings |
| `grep -r "suspicious" /mnt/evidence/` | Search across mounted evidence |
| `find /mnt/evidence -name "*.docx"` | Find specific file types |
| `stat /mnt/evidence/suspicious.doc` | Display file metadata and timestamps |
