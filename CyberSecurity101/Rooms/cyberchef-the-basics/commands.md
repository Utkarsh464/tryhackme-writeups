# CyberChef: The Basics — Commands

CyberChef is a web-based GUI tool and does not have a command-line interface. However, the following describe operations available within CyberChef that function similarly to command-line utilities:

| Operation | Equivalent CLI Tool | Purpose |
|-----------|-------------------|---------|
| To Base64 | base64 (Linux) | Encode data to Base64 |
| From Base64 | base64 -d (Linux) | Decode Base64 data |
| To Hex | xxd -p (Linux) | Encode data to hexadecimal |
| From Hex | xxd -r -p (Linux) | Decode hexadecimal data |
| To Binary | xxd -b (Linux) | Encode data to binary |
| From Binary | Custom script | Decode binary data |
| URL Encode | curl --data-urlencode | Encode URL-unsafe characters |
| URL Decode | python3 -c "import urllib.parse; print(urllib.parse.unquote('...'))" | Decode URL-encoded strings |
| MD5 | md5sum (Linux) | Compute MD5 hash |
| SHA1 | sha1sum (Linux) | Compute SHA1 hash |
| SHA256 | sha256sum (Linux) | Compute SHA256 hash |
| AES Encrypt | openssl enc -aes-256-cbc | Encrypt data with AES |
| AES Decrypt | openssl enc -d -aes-256-cbc | Decrypt AES-encrypted data |
| Gzip | gzip (Linux) | Compress data |
| Gunzip | gunzip (Linux) | Decompress data |
| Regex | grep -P (Linux) | Extract data using regular expressions |
| XOR | Custom Python script | Apply XOR operation to data |
