# CyberChef: The Basics — Tasks

## Task 1: Introduction to CyberChef
Read about the CyberChef project, its origin at GCHQ, and its role as a browser-based data transformation tool. Launch the CyberChef instance and familiarize yourself with the layout: the operation list on the left, the recipe pane in the center, the input pane on the top right, and the output pane on the bottom right.

## Task 2: Basic Encoding and Decoding
Encode a plaintext string into Base64. Then decode a provided Base64 string back to plaintext. Repeat the exercise with hexadecimal encoding and binary encoding. Observe how the output size changes with each encoding scheme.

## Task 3: URL Encoding and Decoding
Use CyberChef to URL-encode a string containing special characters. Decode a URL-encoded string back to its original form. Understand why URL encoding is necessary in web requests and how it can hide malicious payloads.

## Task 4: Hashing Operations
Compute the MD5, SHA1, SHA256, and SHA512 hashes of a given input string. Observe the differences in output length. Discuss the properties of cryptographic hash functions: determinism, preimage resistance, collision resistance, and the avalanche effect.

## Task 5: Encryption and Decryption
Encrypt a plaintext string using AES in ECB mode with a provided key. Decrypt the ciphertext back to the original plaintext using the same key. Repeat the exercise using AES in CBC mode with an initialization vector. Understand the difference between ECB and CBC modes and the importance of IVs.

## Task 6: Recipes and Operation Chaining
Build a multi-step recipe that first Base64-decodes a string, then decompresses the result with gzip, and finally extracts all email addresses using a regular expression. Learn to drag and drop operations, reorder them, and understand how data flows through the recipe pipeline.

## Task 7: Conditional Operations
Use CyberChef's conditional operations (e.g., Drop bytes, Take bytes, Filter) to extract specific portions of data. Learn how to branch recipes and apply different operations based on data content.

## Task 8: The Magic Wand
Use CyberChef's "Magic" operation to automatically detect the encoding or transformation applied to an unknown blob of data. Let the tool suggest the most likely decoding recipe. Compare the tool's suggestion with manual decoding.

## Task 9: Real-World Scenario — Malware Analysis
Given a string that appears to be obfuscated with multiple layers of encoding (Base64, hex, XOR), use CyberChef to peel back each layer and reveal the hidden indicator of compromise. Document each step of the recipe.

## Task 10: Practical Exercises
Complete a set of challenge questions that require building specific CyberChef recipes to achieve a desired output. These exercises test your ability to select the right operations and order them correctly.
