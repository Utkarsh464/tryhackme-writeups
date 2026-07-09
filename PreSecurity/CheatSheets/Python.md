# Python Cheat Sheet

## Basic Syntax
| Code | Description |
|------|-------------|
| `print("hello")` | Print |
| `input("prompt: ")` | User input |
| `len(list)` | Length |
| `type(var)` | Type check |
| `str()`, `int()`, `bool()` | Type casting |

## Data Structures
| Code | Description |
|------|-------------|
| `[]` | List (mutable) |
| `{}` | Dict (key-value) |
| `()` | Tuple (immutable) |
| `set()` | Set (unique items) |
| `list.append(x)` | Add to end |
| `list.pop()` | Remove from end |
| `dict['key']` | Access value |
| `dict.get('key', default)` | Safe access |

## Control Flow
| Code | Description |
|------|-------------|
| `if condition:` | If |
| `elif condition:` | Else if |
| `else:` | Else |
| `for i in iterable:` | For loop |
| `while condition:` | While loop |
| `break` | Exit loop |
| `continue` | Skip iteration |
| `try: except:` | Error handling |
| `with open(f) as fh:` | Context manager |

## String Operations
| Code | Description |
|------|-------------|
| `s.upper()` / `s.lower()` | Case change |
| `s.strip()` | Remove whitespace |
| `s.split(delim)` | Split to list |
| `delim.join(list)` | Join to string |
| `s.replace(a, b)` | Replace substring |
| `s[start:stop:step]` | Slice |
| `f"value {var}"` | f-string |

## Common Libraries
| Library | Usage |
|---------|-------|
| `import requests` | HTTP requests |
| `import socket` | Networking |
| `import subprocess` | System commands |
| `import os` | OS interaction |
| `import sys` | System/argv |
| `import re` | Regular expressions |
| `import json` | JSON processing |
| `import base64` | Base64 encode/decode |
| `import hashlib` | Hashing |
| `import threading` | Threads |