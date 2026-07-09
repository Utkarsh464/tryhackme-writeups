# Tasks: Data Encoding

## Task 1: ASCII
**Purpose:** Understand the ASCII standard for text representation.

**Skills:** 7-bit encoding, ASCII table.

**Theory:** ASCII maps 128 characters (0-127) to numeric values including letters, digits, punctuation, and control codes. Each character takes 1 byte but only uses 7 bits. Extended ASCII adds characters 128-255.

**Commands:** `man ascii`

---

## Task 2: Unicode
**Purpose:** Learn how Unicode supports characters from all writing systems.

**Skills:** Unicode, UTF-8, UTF-16.

**Theory:** Unicode provides a universal character set with over 143,000 characters. UTF-8 is variable-length (1-4 bytes per character) and backward-compatible with ASCII. UTF-16 uses 2 or 4 bytes per character.

**Commands:** None

---

## Task 3: Base64
**Purpose:** Encode binary data as ASCII text using base64.

**Skills:** Base64 encoding/decoding.

**Theory:** Base64 converts binary data into a 64-character subset (A-Z, a-z, 0-9, +, /). It is used for email attachments (MIME), HTTP Basic Authentication, and data URIs in web pages. Every 3 bytes become 4 base64 characters.

**Commands:** `echo "text" | base64`, `echo "dGV4dA==" | base64 -d`

---

## Task 4: URL Encoding
**Purpose:** Encode special characters in URLs.

**Skills:** Percent-encoding.

**Theory:** URL encoding replaces unsafe or reserved characters with % followed by their hex value. For example, space becomes %20, / becomes %2F. It is essential for passing data safely in query strings and URL paths.

**Commands:** `python3 -c "import urllib.parse; print(urllib.parse.quote('hello world'))"`

---

## Task 5: Hex Encoding
**Purpose:** Represent binary data as hexadecimal strings.

**Skills:** Hex encoding.

**Theory:** Hex encoding converts each byte into its two-character hex representation (e.g., 0xFF). It is commonly used in CTF challenges, packet captures, and low-level data analysis.

**Commands:** `echo -n "hello" | xxd -p`, `echo "68656c6c6f" | xxd -r -p`

---
