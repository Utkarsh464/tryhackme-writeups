# base64

## Syntax
`base64 [options] [file]`
`echo "data" | base64`

## Purpose
Encodes or decodes Base64 data. Commonly used for encoding binary data (files, payloads) into ASCII for transmission.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-d` or `--decode` | Decode Base64 data |
| `-w N` | Wrap output at N characters (0 = no wrap) |
| `-i` | Ignore non-alphabet characters during decode |

## Examples
```bash
echo "hello" | base64
echo "aGVsbG8K" | base64 -d
base64 -w0 payload.bin | xclip -sel c
base64 -d encoded.txt > decoded.bin
```

## Compatibility
Linux | macOS