# Commands: Python Basics

## Python Built-in Functions

| Command | Description |
|---------|-------------|
| `print(x)` | Output a value to the console |
| `type(x)` | Return the type of a variable |
| `len(x)` | Return the length of a sequence |
| `input()` | Read user input as a string |
| `range(start, stop, step)` | Generate a sequence of numbers |
| `int(x)`, `str(x)`, `float(x)` | Type conversion functions |

## File Operations

| Command | Description |
|---------|-------------|
| `with open("f", "r") as f: f.read()` | Read entire file |
| `with open("f", "w") as f: f.write("text")` | Write text to file |
| `with open("f", "r") as f: f.readlines()` | Read file into list of lines |

## Common Security Library Usage

| Command | Description |
|---------|-------------|
| `import requests; requests.get(url)` | Make HTTP GET request |
| `import hashlib; hashlib.sha256(data.encode()).hexdigest()` | SHA-256 hash |
| `import socket; socket.gethostbyname("example.com")` | DNS lookup |
| `import os; os.system("ls")` | Execute shell command |
| `import subprocess; subprocess.run(["ls", "-la"])` | Run command safely |
