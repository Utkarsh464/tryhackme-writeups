# Concepts: Become a Hacker

## 1. Cyber Kill Chain
A seven-stage model describing the phases of a cyber attack: Reconnaissance, Weaponisation, Delivery, Exploitation, Installation, Command & Control, and Actions on Objectives.

## 2. Reconnaissance
The first kill chain phase where attackers gather information about the target through open-source intelligence, network scanning, or social engineering.

## 3. Weaponisation and Delivery
Weaponisation couples a payload with a delivery mechanism (e.g., exploit + phishing email). Delivery is the transmission of the weaponised payload to the target.

## 4. Exploitation and Installation
Exploitation triggers the payload by taking advantage of a vulnerability. Installation establishes persistent access on the compromised system.

## 5. MITRE ATT&CK
A globally accessible knowledge base of adversary tactics and techniques. Organised as a matrix covering Enterprise, Mobile, and ICS domains.

## 6. Command Injection
A vulnerability where an attacker executes arbitrary commands on the host operating system via a vulnerable application. Occurs when user input is passed unsanitised to a shell.

## 7. Command Chaining
Techniques to execute multiple commands after injection: `;` (sequential), `&&` (AND), `||` (OR), `|` (pipe). Used by attackers to extend control beyond the intended command.

## 8. Input Validation
The practice of ensuring user input meets expected format before processing. Allowlisting is preferred over denylisting. Never trust user input when constructing shell commands.
