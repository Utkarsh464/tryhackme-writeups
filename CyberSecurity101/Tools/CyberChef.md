# CyberChef

## Purpose
CyberChef is a simple, intuitive web application for performing various data transformation, analysis, and manipulation operations. Developed by GCHQ (the UK's intelligence agency), it is described as the "Cyber Swiss Army Knife." CyberChef provides a drag-and-drop interface for assembling operations including encoding/decoding (Base64, hex, URL, ASCII), encryption/decryption (AES, DES, RSA, Blowfish), hashing (MD5, SHA1, SHA256, bcrypt), data parsing (JSON, XML, CSV, PCAP), compression, and network data analysis.

## Installation
CyberChef can be used directly in a browser or run locally:
```bash
# Online version (no installation)
# Visit: https://gchq.github.io/CyberChef/

# Local installation (Node.js required)
git clone https://github.com/gchq/CyberChef.git
cd CyberChef
npm install
npm run build
# Open build/prod/index.html in browser

# Docker
docker run -d -p 8080:80 mpepping/cyberchef

# Kali Linux (pre-installed via apt)
sudo apt install cyberchef
```

## Basic Usage
1. Drag operations from the left panel into the Recipe area
2. Paste input data into the Input pane on the right
3. Output appears automatically in the Output pane
4. Operations are processed in order from top to bottom
5. Use the Bake button to process data manually (if auto-bake is disabled)

## Important Operations
- **Encoding/Decoding**: From Base64, To Base64, URL Decode, URL Encode, Hex, HTML entities, Unicode
- **Encryption/Decryption**: AES (ECB, CBC, CTR, GCM), DES, Triple DES, RSA, Blowfish, Twofish, XOR
- **Hashing**: MD2, MD5, SHA1, SHA2 (all variants), SHA3, HMAC, bcrypt, scrypt, PBKDF2
- **Data Formats**: Parse JSON, XML, CSV, YAML, MsgPack, CBOR
- **Network**: Parse TCP, UDP, TLS, HTTP request/response, IP headers
- **Compression**: Gzip, Deflate, Zlib, Bzip2, LZMA, Snappy, Brotli
- **Extraction**: Extract URLs, email addresses, file paths, IP addresses, dates
- **Other**: Diff, multiple text transformations (reverse, sort, unique, regex, and find/replace)

## Advanced Features
- **Magic Wand** - Automatically detects encoding/encryption and suggests operations
- **Conditional Operations** - Branching logic based on input conditions
- **Flow Control** - Jumplist, loops, and sub-recipes for complex workflows
- **Chef Profiles** - Save recipes for later use, export/import as JSON
- **Large File Support** - Process files up to several hundred MB in the browser
- **Highway** - In-memory processing using Web Workers for performance
- **Keyboard Shortcuts** - Ctrl+Enter to bake, Ctrl+Shift+D to toggle dark mode

## Typical Workflow
1. During a security assessment, you get encoded data (e.g., Base64) or encrypted content
2. Try the Magic Wand to automatically detect the encoding/encryption scheme
3. If Magic finds the scheme, review the suggested recipe and apply it to additional data
4. For multiple transformations, chain operations in the recipe:
   - Example: Reverse string > From Base64 > Parse JSON > Extract IP addresses
5. For PCAP analysis, parse network packets and extract specific data
6. For CTF challenges, chain XOR with brute-force to find encryption keys
7. Save complex recipes as Chef Profiles for reuse across multiple investigations

## Advantages
- No installation required for web version (runs entirely in browser)
- Data never leaves the client (privacy-focused)
- Extremely wide range of operations in one interface
- Intuitive drag-and-drop recipe building
- Operations can be saved, shared, and imported
- Active open-source community contributing new operations
- Handles large files through efficient browser memory management

## Limitations
- Browser-based processing is slower than native tools for large files
- Some cryptographic operations require knowing the key/IV
- Not designed for automated/scripted use (no CLI)
- No built-in API for integration with other tools
- Complex operations can be confusing to wire up correctly
- Limited to what runs in a JavaScript environment

## Industry Use
CyberChef is used by SOC analysts for log analysis and indicator extraction, by CTF participants for solving challenges, by forensics examiners for data carving and evidence processing, by malware analysts for decoding obfuscated payloads, and by penetration testers for quick data transformation tasks.

## Official Documentation
- Official Site: https://gchq.github.io/CyberChef/
- GitHub: https://github.com/gchq/CyberChef
- Operation Reference: https://gchq.github.io/CyberChef/#op=ListOperations
- Recipe Library: https://github.com/mattnotmax/cyberchef-recipes
- Blog: https://www.gchq.gov.uk/cyberchef
