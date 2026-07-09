# Metasploit: Meterpreter — Tools

- **Metasploit Framework:** Provides the Meterpreter payload generation and session management infrastructure.
- **Meterpreter:** The advanced in-memory payload that provides post-exploitation capabilities. Includes built-in commands for system interaction, privilege escalation, and credential access.
- **Kiwi (Mimikatz):** Loaded as a Meterpreter extension via `load kiwi`. Performs advanced credential theft including plaintext password extraction from LSASS.
- **PowerShell:** Often used in conjunction with Meterpreter for executing scripts, loading additional tools, and interacting with Windows management interfaces.
- **Incognito:** A Meterpreter extension for token manipulation and impersonation. Can steal tokens from other logged-in users.
- **Railgun:** A Meterpreter extension that allows direct interaction with Windows API functions from Meterpreter scripts.
