# CAPA: The Basics — Tasks

## Task 1: Introduction to CAPA
Learn about the CAPA project, its origins at Mandiant, and its purpose in the malware analysis workflow. Understand the difference between signature-based detection and capability-based analysis.

## Task 2: Installation and Setup
Install CAPA on your analysis environment. On Linux, this may involve cloning the GitHub repository and installing Python dependencies. Verify the installation by running `capa --help` and confirming the version.

## Task 3: Running CAPA on a Benign Executable
Download a known benign executable (e.g., notepad.exe or a simple compiled C program). Run CAPA against it using `capa sample.exe`. Examine the output and note which capabilities are reported. Discuss why benign software may trigger certain capability detections.

## Task 4: Running CAPA on a Malicious Sample
Obtain a provided malware sample (or use a test file from the room). Run CAPA and observe the output. Note the difference in the number and type of capabilities compared to the benign sample. Identify capabilities related to persistence, evasion, and C2 communication.

## Task 5: Understanding CAPA Output
Explore each section of the CAPA report: the metadata header (including the estimated attack vector), the list of matched capabilities organized by namespace, and the functions or addresses where each capability was detected. Learn how to read the confidence indicators.

## Task 6: Exploring CAPA Rules
Navigate the CAPA rules directory (`capa/rules/`). Open several rule files and understand their structure: metadata (author, rule name, description), features (strings, API calls, sections), and logic (AND/OR conditions). Identify how rules map to specific capabilities.

## Task 7: Using CAPA with Other Tools
Combine CAPA with other static analysis tools. For example, run strings on the same sample and cross-reference identified strings with CAPA's reported capabilities. Discuss how multiple tools working together provide a more complete picture.

## Task 8: Attack Vector Classification
Understand how CAPA estimates the attack vector of a sample (e.g., Ransomware, Loader, Dropper, Backdoor, Keylogger). Examine what combinations of capabilities lead to each classification and why this is useful for triage.

## Task 9: Writing a Custom CAPA Rule
Create a simple custom CAPA rule that detects a specific behavior, such as writing to the Windows registry Run key for persistence. Test your rule against a sample that exhibits this behavior and verify that it matches.

## Task 10: Capstone — Triage Exercise
Given a set of five unknown binaries, use CAPA to triage each one. For each sample, record the number of capabilities detected, the estimated attack vector, and a priority level (low, medium, high, critical). Compare your triage results with the known classifications provided by the room.
