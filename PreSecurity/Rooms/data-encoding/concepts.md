# Concepts: Data Encoding

## 1. ASCII
American Standard Code for Information Interchange. A 7-bit character encoding standard that defines 128 characters including control codes (0-31), printable characters (32-126), and DEL (127).

## 2. Unicode
A universal character encoding standard that assigns a unique code point to every character across all writing systems. It solves the limitations of ASCII for international text.

## 3. UTF-8
A variable-width Unicode encoding using 1-4 bytes per character. It is the dominant encoding on the web, backward-compatible with ASCII, and space-efficient for Latin scripts.

## 4. UTF-16
A Unicode encoding using 2 bytes for most characters and 4 bytes (surrogate pairs) for less common ones. Used internally by Windows and Java.

## 5. Base64
A binary-to-text encoding scheme that represents binary data in an ASCII string format. Every 3 bytes of input produce 4 base64 characters, with = padding if needed.

## 6. URL Encoding (Percent-Encoding)
A mechanism for encoding information in a Uniform Resource Identifier by replacing unsafe characters with % followed by two hexadecimal digits.

## 7. Hex Encoding
A method of representing binary data as hexadecimal characters. Each byte (8 bits) is represented by two hex digits (0-9, A-F).

## 8. Control Characters
Non-printable ASCII characters (0-31) used for device control, including null (0x00), newline (0x0A), carriage return (0x0D), and tab (0x09).
