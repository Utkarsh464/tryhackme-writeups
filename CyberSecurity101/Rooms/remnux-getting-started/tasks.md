# REMnux: Getting Started — Tasks

## Task 1: Introduction to REMnux
Learn about the REMnux project, its history, and its role in the malware analysis community. Understand the difference between REMnux, Kali Linux, and other security distributions. Review the system requirements for running REMnux.

## Task 2: Installation and Setup
Download the latest REMnux virtual machine image or OVA file. Import it into your hypervisor (VirtualBox, VMware, or Hyper-V). Boot the VM and log in with the default credentials. Alternatively, explore the Docker-based REMnux container option.

## Task 3: Exploring the Desktop Environment
Navigate the REMnux desktop. Locate the application menus organized by category: Malware Analysis, Forensics, Network, Reverse Engineering, and Utilities. Open the terminal and verify the OS details with `lsb_release -a` and `uname -a`.

## Task 4: Static PE Analysis
Use the `file` command to identify a sample binary's type. Run `strings` to extract human-readable strings and look for suspicious indicators. Use `radare2` to examine the binary's sections, imports, and exports. Compare your findings with a known-good sample.

## Task 5: Analyzing Office Documents
Use `oledump.py` or `oleid` to scan a suspicious Word document for embedded objects and macros. Use `olevba` to extract and analyze VBA macro code. Look for AutoOpen, Shell, and download functions that indicate malicious intent. Use `mraptor` to assess macro risk.

## Task 6: Analyzing PDF Files
Use `pdfid.py` to scan a PDF for key indicators such as embedded files, JavaScript, and launch actions. Use `pdf-parser.py` to extract and examine specific objects within the PDF structure. Identify objects that contain encoded or obfuscated JavaScript.

## Task 7: Basic Memory Analysis
Install or locate Volatility on REMnux. Use `volatility -f memory.dump imageinfo` to identify the operating system profile. Use `volatility pslist` to list running processes and `volatility netscan` to identify network connections at the time of capture.

## Task 8: Network Traffic Analysis
Use `tcpdump` to capture live traffic on the REMnux interface. Use Wireshark to open a pre-captured pcap file from a malware infection scenario. Filter traffic by IP address, protocol, and port. Follow TCP streams to examine HTTP requests and responses.

## Task 9: Combining Tools in a Workflow
Analyze a provided suspicious file using a complete workflow: identify the file type, extract strings, scan with CAPA, examine with radare2, and check for network indicators. Document each step and the findings from each tool. Discuss how the tools complement each other.

## Task 10: REMnux Tool Discovery
Explore less commonly used tools bundled with REMnux. Research what tools are available in the Forensics and Reverse Engineering menus. Try at least two tools you have not used before and document what they do.
