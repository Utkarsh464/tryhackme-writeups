# CyberChef: The Basics — Concepts

## Data Encoding
The process of converting data from one format to another for transmission, storage, or obfuscation. Common encodings include Base64, hexadecimal, binary, and URL encoding. Encoding is not encryption — it does not provide confidentiality; it merely changes the representation of data.

## Base64 Encoding
A binary-to-text encoding scheme that represents binary data in an ASCII string format using a 64-character alphabet. Base64 is commonly used in email attachments (MIME), storing binary data in JSON or XML, and by malware authors to obfuscate strings and payloads.

## Hexadecimal Representation
A base-16 numbering system that uses digits 0-9 and letters A-F to represent binary data in a human-readable form. Each hex digit represents 4 bits. Hex is commonly used in debugging, memory dumps, and network packet analysis.

## Cryptographic Hash Functions
Functions that take an input and produce a fixed-size output (digest) that is unique to the input. Properties include determinism (same input always produces the same output), preimage resistance (cannot reverse the hash to find the input), collision resistance (two different inputs should not produce the same hash), and the avalanche effect (a small change in input produces a completely different output). Common hash functions include MD5 (128-bit), SHA1 (160-bit), and SHA256 (256-bit).

## Symmetric Encryption
Encryption that uses the same key for both encryption and decryption. AES (Advanced Encryption Standard) and DES (Data Encryption Standard) are symmetric ciphers. Modes include ECB (Electronic Codebook), where each block is encrypted independently, and CBC (Cipher Block Chaining), where each block is XORed with the previous ciphertext before encryption. CBC requires an initialization vector (IV) and is generally more secure than ECB.

## Operation Recipes
A sequence of CyberChef operations chained together to transform data through multiple steps. Recipes are created by dragging operations from the operation list into the recipe pane and configuring their parameters. The output of one operation becomes the input to the next.

## Magic Operation
CyberChef's automated analysis feature that attempts to detect the encoding or transformation applied to input data and suggests the most likely decoding recipe. It works by analyzing the data's characteristics (character set, entropy, structure) and trying common decoding operations.
