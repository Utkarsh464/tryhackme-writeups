# Tasks: Become a Hacker

## Task 1: Cyber Kill Chain
**Purpose:** Understand the stages of a cyber attack.

**Skills:** Reconnaissance, Weaponisation, Delivery, Exploitation, Installation, C2, Actions on Objectives.

**Theory:** Developed by Lockheed Martin, the Cyber Kill Chain describes seven stages attackers follow. Reconnaissance gathers information, Weaponisation creates the payload, Delivery transmits it, Exploitation triggers it, Installation establishes persistence, C2 (Command & Control) enables remote access, and Actions on Objectives achieves the goal.

**Commands:** None

---

## Task 2: MITRE ATT&CK
**Purpose:** Learn to use the MITRE ATT&CK framework for attack classification.

**Skills:** Tactics, techniques, sub-techniques, mitigations.

**Theory:** MITRE ATT&CK is a knowledge base of adversary tactics and techniques based on real-world observations. Tactics are the "why" (e.g., Initial Access), techniques are the "how" (e.g., Phishing). Each technique has sub-techniques and recommended mitigations.

**Commands:** None

---

## Task 3: Command Injection
**Purpose:** Exploit a web application with command injection.

**Skills:** Unsanitised input, system() calls, command chaining.

**Theory:** Command injection occurs when user input is passed to a system shell without sanitisation. The classic example is a ping form that passes the IP directly to `ping`. Attackers can chain commands using `;`, `&&`, `||`, or `|`.

**Commands:** `127.0.0.1; ls`, `127.0.0.1 && whoami`

---

## Task 4: Input Validation Defence
**Purpose:** Implement defences against command injection.

**Skills:** Input validation, allowlisting, parameterised APIs.

**Theory:** Validate input by allowlisting permitted characters (e.g., only digits and dots for an IP field). Avoid passing user input directly to shell functions. Use language-specific APIs that don't invoke a shell, such as Python's `subprocess.run` with a list argument.

**Commands:** None

---

## Task 5: OS Command vs Code Injection
**Purpose:** Distinguish between command injection and code injection.

**Skills:** Injection classification.

**Theory:** OS command injection executes operating system commands through a shell. Code injection executes code in the application's language (e.g., PHP eval, SQL injection, JavaScript eval). Both stem from untrusted data being interpreted as code.

**Commands:** None

---
