# CyberChef: The Basics — Tools

## CyberChef
- **Description:** CyberChef is a web-based application developed by GCHQ for data transformation, analysis, and manipulation. It is often described as the "Cyber Swiss Army Knife" because of its extensive library of operations covering encoding, decoding, encryption, decryption, hashing, compression, data extraction, and more.
- **Website:** https://gchq.github.io/CyberChef/
- **Key Features:**
  - Drag-and-drop recipe interface for building data transformation pipelines
  - Over 300 operations including Base64, hex, binary, URL encoding/decoding
  - Symmetric encryption and decryption (AES, DES, Blowfish, etc.)
  - Cryptographic hash functions (MD5, SHA1, SHA256, SHA512)
  - Compression and decompression (gzip, zlib, bzip2)
  - Regular expression extraction and filtering
  - Conditional logic (drop, take, filter, find/replace)
  - Magic wand for automatic decoding detection
  - Diff tool for comparing two inputs
  - Support for large files and streaming data
  - No installation required — runs entirely in the browser
- **Use Cases:** Malware analysis, forensic investigation, log analysis, CTF challenges, data format conversion, and general data manipulation tasks.

## How CyberChef Compares to CLI Alternatives
While command-line tools like `base64`, `openssl`, and `grep` offer similar individual functions, CyberChef's key advantage is its visual recipe interface that chains operations without scripting. A complex decoding pipeline that would require piping data through multiple command-line tools with careful argument handling can be built in CyberChef with drag-and-drop simplicity. This makes it especially valuable for analysts who need to quickly experiment with different decoding strategies, share reproducible recipes with team members, or work with data formats they encounter infrequently. CyberChef recipes can be exported as URLs or JSON, enabling collaborative analysis and repeatable forensic workflows. The tool is also entirely client-side — no data is uploaded to any server — making it suitable for working with sensitive or classified information in air-gapped environments when run locally.
