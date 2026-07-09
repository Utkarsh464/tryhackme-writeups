# John the Ripper: The Basics — Tasks

## Task 1: Introduction and Hash Identification
- **Purpose:** Learn to identify different hash types before cracking.
- **Skills:** Hash format recognition, hash-identifier usage.
- **Commands:** `john --list=formats`, `hash-identifier`, `hashid`
- **Theory:** John the Ripper needs to know the hash format to crack it correctly. Hash identifiers analyze the hash format (length, character set, prefix) to guess the type. Common formats include raw-md5, raw-sha256, bcrypt, descrypt, nt, and lm.

## Task 2: Dictionary Attack
- **Purpose:** Crack password hashes using a wordlist.
- **Skills:** Wordlist selection, basic john syntax.
- **Commands:** `john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt`, `john hash.txt`
- **Theory:** A dictionary attack tries each word from a wordlist as the password. RockYou is the most common wordlist. John automatically detects the hash format and tries the hashing algorithm against each word. If run without --wordlist, John uses its default password.lst.

## Task 3: Rule-Based Attacks
- **Purpose:** Use rules to mutate wordlist entries for more effective cracking.
- **Skills:** Rule selection, custom rule understanding.
- **Commands:** `john --wordlist=words.txt --rules=best64 hash.txt`, `john --wordlist=words.txt --rules=KoreLogicRules hash.txt`
- **Theory:** Rules apply transformations to each wordlist entry: appending digits, capitalizing letters, substituting characters (e.g., a->@, s->$), and concatenating words. The best64 rule set contains the 64 most effective rules. Custom rules can be defined in john.conf.

## Task 4: Incremental (Brute-Force) Mode
- **Purpose:** Crack passwords by trying all possible character combinations.
- **Skills:** Incremental mode configuration, trade-off understanding.
- **Commands:** `john --incremental hash.txt`, `john --incremental=LowerNum hash.txt`
- **Theory:** Incremental mode tries every possible combination of characters. It is guaranteed to find the password eventually but is extremely slow for long or complex passwords. John uses precomputed character frequency statistics to try the most likely combinations first. Modes: ASCII (all printable), LowerNum, Alpha, etc.

## Task 5: Cracking Specific Formats
- **Purpose:** Crack different hash types commonly encountered in CTFs.
- **Skills:** Format specification, hash file preparation.
- **Commands:** `john --format=raw-md5 hash.txt`, `john --format=nt hash.txt`, `john --format=bcrypt hash.txt`
- **Theory:** Different applications use different hash formats. Unix /etc/shadow uses $id$salt$hash format. Windows stores NTLM hashes. Web applications often use MD5 or SHA. John can crack any of these when the correct format is specified.
