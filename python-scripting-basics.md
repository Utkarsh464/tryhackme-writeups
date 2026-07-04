# TryHackMe Python Scripting Basics — Comprehensive Write-up

- **Module:** Python Scripting Basics
- **Difficulty:** Beginner
- **Estimated Completion Time:** 3–5 hours
- **Status:** ✅ In Progress (2/4 rooms completed)
- **Profile:** [utkarsshh](https://tryhackme.com/p/utkarsshh)

---

## Table of Contents

1. [Python: Simple Demo](#1-python-simple-demo)
2. [Python: Core Concepts](#2-python-core-concepts)
3. [Python: Building Scripts](#3-python-building-scripts)
4. [Python: Pentesting Scripts](#4-python-pentesting-scripts)
5. [Topic Transition Recap](#5-topic-transition-recap)
6. [Final Thoughts](#6-final-thoughts)

---

## 1. Python: Simple Demo

### Overview

This room provides a gentle introduction to the Python interpreter and the syntax of the language. No prior programming experience is assumed. The goal is to write and execute a basic Python program, understand the print function, and get comfortable with the interactive shell.

### Getting Started

Python can be run in two modes:

- **Interactive mode:** Launch the REPL by typing `python3` in a terminal. Commands are executed immediately.
- **Script mode:** Write code to a `.py` file and execute it with `python3 filename.py`.

```python
# Hello, World!
print("Hello, World!")
```

```bash
python3 hello.py
# Output: Hello, World!
```

### Key Concepts

**The `print()` function:**

The most basic output mechanism. It accepts one or more arguments and writes them to stdout:

```python
print("Hello, THM!")
print("Python", "is", "fun", sep="-")   # Custom separator
print("No newline", end="")              # Suppress newline
```

**Comments:**

```python
# This is a single-line comment

"""
This is a
multi-line comment
(technically a string literal)
"""
```

**Basic Arithmetic:**

```python
print(2 + 3)      # 5
print(10 - 4)     # 6
print(3 * 7)      # 21
print(10 / 3)     # 3.333...
print(10 // 3)    # 3 (integer division)
print(10 % 3)     # 1 (modulo)
print(2 ** 10)    # 1024 (exponentiation)
```

**Getting User Input:**

```python
name = input("What is your name? ")
print(f"Hello, {name}!")
```

**Type Checking:**

```python
print(type(42))       # <class 'int'>
print(type(3.14))     # <class 'float'>
print(type("text"))   # <class 'str'>
print(type(True))     # <class 'bool'>
```

### Practical Exercises

1. Write a script that asks for the user's name and age, then prints a greeting with their age in dog years.
2. Create a simple calculator that takes two numbers and prints their sum, difference, product, and quotient.
3. Use the interactive REPL to experiment with different arithmetic operators and observe the output.

### Key Takeaways

- Python is interpreted — no compilation step required.
- The REPL is excellent for experimentation and debugging.
- `print()` and `input()` are the primary I/O functions.
- Python dynamically types variables; `type()` reveals the underlying type.

---

## 2. Python: Core Concepts

### Overview

This room builds foundational programming knowledge — variables, data types, control flow, functions, and data structures. These concepts are the building blocks of every Python script.

### Variables and Data Types

Variables are named references to objects in memory:

```python
name = "Alice"        # str
age = 25              # int
height = 1.68         # float
is_student = True     # bool
hobbies = None        # NoneType
```

**Type conversion:**

```python
age_str = str(25)           # "25"
age_num = int("25")         # 25
pi = float("3.14")          # 3.14
truthy = bool(1)            # True
falsy = bool(0)             # False
```

**String operations:**

```python
greeting = "Hello, " + name         # Concatenation
repeat = "Ha" * 3                   # "HaHaHa"
length = len(greeting)              # String length
upper = greeting.upper()            # "HELLO, ALICE"
parts = "a,b,c".split(",")          # ["a", "b", "c"]
joined = "-".join(["a", "b", "c"])  # "a-b-c"
```

### Control Flow

**Conditionals (`if`/`elif`/`else`):**

```python
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
else:
    grade = "F"

print(f"Grade: {grade}")
```

**Comparison and logical operators:**

| Operator | Meaning | Example |
|----------|---------|---------|
| `==` | Equal to | `5 == 5` → `True` |
| `!=` | Not equal | `5 != 3` → `True` |
| `>` | Greater than | `5 > 3` → `True` |
| `<` | Less than | `5 < 3` → `False` |
| `>=` | Greater than or equal | `5 >= 5` → `True` |
| `<=` | Less than or equal | `5 <= 3` → `False` |
| `and` | Logical AND | `True and False` → `False` |
| `or` | Logical OR | `True or False` → `True` |
| `not` | Logical NOT | `not True` → `False` |

**Loops:**

`for` loop — iterate over a sequence:

```python
# Range
for i in range(5):
    print(i)          # 0, 1, 2, 3, 4

# List
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# Enumerate (index + value)
for idx, fruit in enumerate(fruits):
    print(f"{idx}: {fruit}")
```

`while` loop — repeat until a condition is false:

```python
count = 0
while count < 5:
    print(count)
    count += 1
```

**Loop control:**

```python
for i in range(10):
    if i == 3:
        continue      # Skip iteration
    if i == 7:
        break         # Exit loop entirely
    print(i)
```

### Functions

Functions encapsulate reusable logic:

```python
def greet(name, greeting="Hello"):
    """Return a personalised greeting."""
    return f"{greeting}, {name}!"

print(greet("Alice"))           # Hello, Alice!
print(greet("Bob", "Hi"))       # Hi, Bob!
```

**Keyword arguments:**

```python
def describe_pet(animal, name):
    print(f"I have a {animal} named {name}.")

describe_pet(animal="dog", name="Rex")
describe_pet(name="Whiskers", animal="cat")
```

**Variable scope:**

```python
x = "global"

def my_func():
    x = "local"       # Shadows global x
    print(x)

my_func()             # local
print(x)              # global
```

**Lambda (anonymous) functions:**

```python
square = lambda x: x ** 2
print(square(5))      # 25

# Often used with map/filter
numbers = [1, 2, 3, 4]
squared = list(map(lambda x: x ** 2, numbers))
```

### Data Structures

**Lists — ordered, mutable sequences:**

```python
fruits = ["apple", "banana", "cherry"]
fruits.append("date")              # Add to end
fruits.insert(1, "blueberry")      # Insert at index
fruits.remove("banana")            # Remove by value
popped = fruits.pop()              # Remove and return last
fruits.sort()                      # Sort in place
fruits.reverse()                   # Reverse in place
sliced = fruits[1:3]               # Slice (index 1 to 2)
```

**Tuples — ordered, immutable:**

```python
point = (3, 4)
x, y = point                       # Unpacking
# point[0] = 5                     # TypeError!
```

**Dictionaries — key-value pairs:**

```python
user = {
    "name": "Alice",
    "age": 25,
    "skills": ["Python", "Linux"]
}

print(user["name"])                # Alice
user["age"] = 26                   # Update
user["city"] = "London"            # Add new key
del user["city"]                   # Delete
for key, value in user.items():
    print(f"{key}: {value}")
```

**Sets — unordered, unique elements:**

```python
unique = {1, 2, 3, 3, 2}          # {1, 2, 3}
unique.add(4)
a = {1, 2, 3}
b = {3, 4, 5}
print(a & b)                       # Intersection: {3}
print(a | b)                       # Union: {1, 2, 3, 4, 5}
print(a - b)                       # Difference: {1, 2}
```

**List comprehensions:**

```python
squares = [x ** 2 for x in range(10)]
evens = [x for x in range(20) if x % 2 == 0]
matrix = [[i * j for j in range(3)] for i in range(3)]
```

### Exception Handling

```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
    print(f"Result: {result}")
except ValueError:
    print("That's not a valid number!")
except ZeroDivisionError:
    print("Cannot divide by zero!")
else:
    print("No errors occurred.")
finally:
    print("This always runs.")
```

### File I/O

```python
# Reading
with open("data.txt", "r") as f:
    content = f.read()             # Entire file
    lines = f.readlines()          # List of lines
    for line in f:                 # Iterate line by line
        print(line.strip())

# Writing
with open("output.txt", "w") as f:
    f.write("Hello, file!\n")

# Appending
with open("log.txt", "a") as f:
    f.write("New log entry\n")
```

### Key Takeaways

- Everything in Python is an object — variables, functions, even types themselves.
- Indentation defines blocks; consistency matters (4 spaces is standard).
- Functions should do one thing and be named descriptively.
- Lists, dicts, and sets are the most commonly used data structures in scripting.
- Use `with` for file I/O — it automatically handles cleanup.

---

## 3. Python: Building Scripts

### Overview

This room transitions from learning syntax to writing standalone, practical scripts. Topics include argument parsing, modular code organisation, working with external libraries, and error handling for production-quality scripts.

### Script Structure

A well-organised Python script follows a consistent pattern:

```python
#!/usr/bin/env python3
"""Description of what this script does."""

import sys
import argparse


def parse_args():
    """Parse command-line arguments."""
    parser = argparse.ArgumentParser(
        description="Process some input."
    )
    parser.add_argument("input", help="Input file path")
    parser.add_argument("-o", "--output", help="Output file path")
    parser.add_argument("-v", "--verbose", action="store_true",
                        help="Enable verbose output")
    return parser.parse_args()


def main():
    args = parse_args()
    if args.verbose:
        print(f"Processing {args.input}...")
    # Script logic here
    print(f"Output written to {args.output or 'stdout'}")


if __name__ == "__main__":
    main()
```

The `if __name__ == "__main__":` guard ensures code only runs when the script is executed directly, not when imported as a module.

### Command-Line Arguments

**Using `sys.argv`:**

```python
import sys

script_name = sys.argv[0]
arguments = sys.argv[1:]

if len(arguments) < 1:
    print("Usage: python script.py <name>")
    sys.exit(1)

print(f"Hello, {arguments[0]}!")
```

**Using `argparse` (recommended):**

```python
import argparse

parser = argparse.ArgumentParser(description="Network scanner")
parser.add_argument("target", help="Target IP or hostname")
parser.add_argument("-p", "--ports", type=int, nargs="+",
                    default=[22, 80, 443], help="Ports to scan")
parser.add_argument("-t", "--timeout", type=float, default=1.0,
                    help="Connection timeout in seconds")
parser.add_argument("--verbose", action="store_true")

args = parser.parse_args()
print(f"Scanning {args.target} on ports {args.ports}")
```

### Working with External Libraries

Install packages using `pip`:

```bash
pip install requests
pip install python-dotenv
```

Track dependencies in a `requirements.txt`:

```
requests==2.31.0
python-dotenv==1.0.0
colorama==0.4.6
```

```bash
pip install -r requirements.txt
```

### Environment Variables and Configuration

```python
import os
from dotenv import load_dotenv

load_dotenv()                      # Load .env file

API_KEY = os.getenv("API_KEY")
DB_HOST = os.getenv("DB_HOST", "localhost")
```

### Logging

Replace `print()` with the `logging` module for production scripts:

```python
import logging

logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s [%(levelname)s] %(message)s",
    handlers=[
        logging.FileHandler("script.log"),
        logging.StreamHandler()
    ]
)

logging.debug("Detailed debug info")
logging.info("Script started")
logging.warning("Disk space low")
logging.error("Failed to connect")
logging.critical("Unrecoverable error")
```

### Modular Code Organisation

Split code into multiple files and import as modules:

```
project/
├── main.py
├── utils/
│   ├── __init__.py
│   ├── network.py
│   └── parsing.py
└── requirements.txt
```

```python
# utils/network.py
def scan_port(host, port):
    """Check if a port is open."""
    ...

# main.py
from utils.network import scan_port
from utils.parsing import parse_targets
```

### Key Takeaways

- Always use `argparse` for handling command-line arguments.
- Structure scripts with a `main()` function and `if __name__` guard.
- Use the `logging` module for production-grade output.
- Split large scripts into modules with clear responsibilities.
- Pin dependency versions in `requirements.txt`.

---

## 4. Python: Pentesting Scripts

### Overview

This room applies Python scripting skills to real penetration testing scenarios. The focus is on building tools for web recon, network scanning, hash cracking, and SSH brute-forcing — tasks that pentesters perform routinely on engagements.

### Web Reconnaissance

**HTTP Requests with `requests`:**

```python
import requests

# Basic GET
response = requests.get("https://example.com")
print(f"Status: {response.status_code}")
print(f"Headers: {response.headers}")
print(f"Body: {response.text[:500]}")

# POST with data
data = {"username": "admin", "password": "password"}
response = requests.post("https://example.com/login", data=data)

# Custom headers
headers = {"User-Agent": "Mozilla/5.0 (X11; Linux x86_64)"}
response = requests.get("https://example.com", headers=headers)

# Handle redirects
response = requests.get("https://example.com", allow_redirects=True)

# Timeout
response = requests.get("https://example.com", timeout=5)
```

**Directory/File Brute-Forcer:**

```python
import requests
import sys

def brute_force_directories(base_url, wordlist_path):
    with open(wordlist_path, "r") as f:
        words = [line.strip() for line in f if line.strip()]

    for word in words:
        url = f"{base_url.rstrip('/')}/{word}"
        try:
            response = requests.get(url, timeout=3)
            if response.status_code == 200:
                print(f"[FOUND] {url} ({len(response.text)} bytes)")
            elif response.status_code == 403:
                print(f"[FORBIDDEN] {url}")
            elif response.status_code == 301:
                print(f"[REDIRECT] {url} -> {response.headers.get('Location')}")
        except requests.exceptions.RequestException as e:
            print(f"[ERROR] {url}: {e}")

if __name__ == "__main__":
    base = sys.argv[1]
    wordlist = sys.argv[2]
    brute_force_directories(base, wordlist)
```

**Subdomain Enumeration:**

```python
import requests
import sys

def enumerate_subdomains(domain, wordlist_path):
    with open(wordlist_path, "r") as f:
        subdomains = [line.strip() for line in f if line.strip()]

    for sub in subdomains:
        url = f"https://{sub}.{domain}"
        try:
            response = requests.get(url, timeout=3)
            if response.status_code < 400:
                print(f"[LIVE] {url} ({response.status_code})")
        except requests.exceptions.ConnectionError:
            pass
        except requests.exceptions.RequestException as e:
            print(f"[ERROR] {url}: {e}")
```

### Network Scanning

**TCP Port Scanner using Sockets:**

```python
import socket
import sys
from concurrent.futures import ThreadPoolExecutor

def scan_port(host, port):
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)
        result = sock.connect_ex((host, port))
        sock.close()
        if result == 0:
            return port
    except Exception:
        pass
    return None

def scan_ports(host, ports, max_workers=50):
    open_ports = []
    with ThreadPoolExecutor(max_workers=max_workers) as executor:
        futures = {executor.submit(scan_port, host, p): p for p in ports}
        for future in futures:
            result = future.result()
            if result:
                open_ports.append(result)
    return sorted(open_ports)

if __name__ == "__main__":
    target = sys.argv[1]
    port_range = range(1, 1025) if len(sys.argv) < 3 else \
                 range(int(sys.argv[2]), int(sys.argv[3]) + 1)

    print(f"Scanning {target} on ports {port_range[0]}-{port_range[-1]}...")
    open_ports = scan_ports(target, port_range)

    if open_ports:
        print(f"Open ports: {', '.join(map(str, open_ports))}")
    else:
        print("No open ports found.")
```

**Service Version Detection (Banner Grabbing):**

```python
import socket

def grab_banner(host, port):
    try:
        sock = socket.socket()
        sock.settimeout(3)
        sock.connect((host, port))
        # Send a probe for common services
        if port == 80 or port == 443:
            sock.send(b"GET / HTTP/1.1\r\nHost: " +
                      bytes(host, 'utf-8') + b"\r\n\r\n")
        elif port == 22:
            pass  # SSH sends banner on connect
        banner = sock.recv(1024).decode(errors="ignore").strip()
        sock.close()
        return banner
    except Exception:
        return None
```

**ICMP Ping Sweep:**

```python
import subprocess
import sys
from concurrent.futures import ThreadPoolExecutor

def ping_host(ip):
    try:
        result = subprocess.run(
            ["ping", "-c", "1", "-W", "1", ip],
            capture_output=True, timeout=2
        )
        return ip if result.returncode == 0 else None
    except subprocess.TimeoutExpired:
        return None

def ping_sweep(subnet):
    live = []
    ips = [f"{subnet}.{i}" for i in range(1, 255)]
    with ThreadPoolExecutor(max_workers=50) as executor:
        futures = [executor.submit(ping_host, ip) for ip in ips]
        for future in futures:
            result = future.result()
            if result:
                live.append(result)
                print(f"[LIVE] {result}")
    return live
```

### Hash Cracking

**Dictionary-based Hash Cracker:**

```python
import hashlib
import sys

def crack_hash(target_hash, wordlist_path, hash_type="md5"):
    hash_func = {
        "md5": hashlib.md5,
        "sha1": hashlib.sha1,
        "sha256": hashlib.sha256,
        "sha512": hashlib.sha512,
    }.get(hash_type)

    if not hash_func:
        print(f"Unsupported hash type: {hash_type}")
        return None

    with open(wordlist_path, "r", encoding="latin-1") as f:
        for line in f:
            word = line.strip()
            computed = hash_func(word.encode()).hexdigest()
            if computed == target_hash:
                return word
    return None

if __name__ == "__main__":
    hash_value = sys.argv[1]
    wordlist = sys.argv[2]
    algo = sys.argv[3] if len(sys.argv) > 3 else "md5"

    result = crack_hash(hash_value, wordlist, algo)
    if result:
        print(f"[SUCCESS] Hash cracked: {result}")
    else:
        print("[FAILED] Hash not found in wordlist")
```

### SSH Brute-Forcing

**SSH Credential Tester using `paramiko`:**

```python
import paramiko
import sys
from concurrent.futures import ThreadPoolExecutor

def try_ssh(host, username, password, port=22):
    client = paramiko.SSHClient()
    client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    try:
        client.connect(host, port=port, username=username,
                       password=password, timeout=5)
        client.close()
        return (username, password, True)
    except paramiko.AuthenticationException:
        return (username, password, False)
    except Exception as e:
        return (username, password, str(e))

def brute_force_ssh(host, username, wordlist_path, port=22):
    with open(wordlist_path, "r", encoding="latin-1") as f:
        passwords = [line.strip() for line in f if line.strip()]

    print(f"Attempting {len(passwords)} passwords for {username}@{host}...")

    with ThreadPoolExecutor(max_workers=10) as executor:
        futures = [
            executor.submit(try_ssh, host, username, pw, port)
            for pw in passwords
        ]
        for future in futures:
            user, pw, result = future.result()
            if result is True:
                print(f"[SUCCESS] {user}:{pw}")
                return
            elif result is not False:
                print(f"[ERROR] {user}:{pw} -> {result}")

    print("[FAILED] No valid credentials found.")

if __name__ == "__main__":
    target = sys.argv[1]
    user = sys.argv[2]
    wordlist = sys.argv[3]
    brute_force_ssh(target, user, wordlist)
```

### Key Takeaways

- The `requests` library is the standard for HTTP interactions in pentesting scripts.
- Socket programming gives fine-grained control for network scanning.
- Threading (`ThreadPoolExecutor`) dramatically speeds up brute-force and scanning tasks.
- `paramiko` provides a Python-native SSH implementation for authentication testing.
- Always handle exceptions gracefully — network operations fail frequently.
- Add rate limiting and polite delays to avoid overwhelming targets or triggering defences.

---

## 5. Topic Transition Recap

This section consolidates key questions from the completed rooms to reinforce learning before advancing.

### Questions from Python: Simple Demo

1. **What function is used to get input from the user?**
   - `input()`

2. **Which library is commonly used for HTTP requests?**
   - `requests`

3. **How do you print output to the console?**
   - `print()`

4. **What is the operator for exponentiation in Python?**
   - `**`

### Questions from Python: Core Concepts

1. **What keyword defines a function in Python?**
   - `def`

2. **How do you open a file in Python?**
   - `open()` or `with open() as f:`

3. **What data structure stores key-value pairs?**
   - Dictionary (`dict`)

4. **What is the difference between a list and a tuple?**
   - Lists are mutable (`[]`), tuples are immutable (`()`).

5. **How do you handle exceptions in Python?**
   - `try`/`except`/`finally` blocks.

6. **What does `len()` return?**
   - The length (number of elements) of a sequence.

7. **How do you add an element to the end of a list?**
   - `list.append(element)`

---

## 6. Final Thoughts

The Python Scripting Basics module delivers exactly what it promises: it takes someone with little to no Python experience and equips them with the skills to write practical, real-world scripts for penetration testing.

### What I Found Most Valuable

1. **Immediate applicability:** Every concept is taught with a pentesting use case in mind. The final room ties everything together into tools you would actually use on an engagement.
2. **Progressive difficulty:** The module moves from `print("Hello")` to multi-threaded port scanners and SSH brute-forcers without feeling rushed. Each room builds naturally on the previous one.
3. **Script-first mentality:** The emphasis on writing standalone scripts (with argument parsing, logging, error handling) rather than just code snippets prepares you for real tool development.

### Next Steps

With Python Scripting Basics completed, the logical next modules are:

| Module | Focus |
|--------|-------|
| **Python for Pentesters** | Advanced tooling, custom exploits, obfuscation |
| **Intro to Web Hacking** | Applying scripting to web application testing |
| **Network Security** | Deeper dive into network-level attacks and defence |
| **Metasploit** | Integrating custom Python scripts with the Metasploit framework |

### Resources for Continued Learning

- **Books:** *Black Hat Python* (Seitz), *Violent Python* (O'Connor), *Automate the Boring Stuff with Python* (Sweigart).
- **Labs:** Hack The Box (starting point machines), PortSwigger Web Security Academy, PicoCTF.
- **Practice:** Write your own versions of common tools (port scanner, directory brute-forcer, hash cracker) and compare them against established tools like nmap, gobuster, and hashcat.

---

*Module started: July 2026*  
*TryHackMe Profile: [utkarsshh](https://tryhackme.com/p/utkarsshh)*  
*Rooms completed: 2/4 (Python: Simple Demo ✅, Python: Core Concepts ✅, Python: Building Scripts 🔄, Python: Pentesting Scripts 🔒)*
