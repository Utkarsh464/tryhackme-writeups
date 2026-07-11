# CAPA: The Basics — Commands

| Command | Description |
|---------|-------------|
| `capa sample.exe` | Run CAPA against a PE file and display all matched capabilities |
| `capa -v sample.exe` | Run CAPA with verbose output showing details of each match |
| `capa -vv sample.exe` | Run CAPA with very verbose output including matched addresses |
| `capa -r rules/ sample.exe` | Run CAPA using a specific rules directory |
| `capa -j sample.exe` | Output results in JSON format for programmatic processing |
| `capa -f sample.exe` | Specify input format (pe, elf, or auto) |
| `capa --tags persistence sample.exe` | Filter output to only show capabilities with specific tags |
| `capa --signatures sample.exe` | Include signature-based detection alongside capability analysis |
| `capa --help` | Display help information for all CAPA command-line options |
| `python3 capa/main.py sample.exe` | Run CAPA directly from the source directory using Python |
| `capa --version` | Display the installed CAPA version |
| `capa --help` | Show detailed help including all options and usage examples |
| `python3 capa/main.py -f pe sample.exe` | Run CAPA explicitly specifying the PE input format |
| `capa --enable-all sample.exe` | Enable all rules including those that might produce noisy results |
| `capa --disable-filter sample.exe` | Disable default filtering to show all potential matches |
| `capa --no-autoload sample.exe` | Run CAPA without automatically loading default rules |

## Usage Examples

To analyze a sample with verbose output: `capa -v suspicious.exe` will display each matched capability along with the specific features (API calls, strings, or section characteristics) that triggered the match. The very verbose mode (`-vv`) adds matched addresses, which is useful when you need to locate the exact code offset where a capability was detected. When processing multiple samples for triage, use the JSON output format (`-j`) to produce machine-readable results that can be ingested by a SIEM or automated analysis pipeline. To filter results to a specific behavior category, use `--tags` followed by the namespace you want to inspect. For example, `capa --tags persistence sample.exe` shows only capabilities related to persistence mechanisms, helping you quickly assess whether a sample will survive a reboot.
