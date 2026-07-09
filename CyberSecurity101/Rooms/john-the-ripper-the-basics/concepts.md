# John the Ripper: The Basics — Concepts

## John the Ripper
An open-source password cracking tool supporting dozens of hash formats. Features multiple cracking modes (dictionary, incremental, rules-based, and external).

## Dictionary Attack
A method that tries each word from a wordlist as the password candidate. Effectiveness depends on wordlist quality and whether the password is a dictionary word or simple variation.

## Wordlist
A file containing a list of potential passwords, one per line. RockYou is the most famous wordlist, containing 14 million passwords from the 2009 social gaming site breach.

## Rule-Based Attack
A method that applies transformation rules to wordlist entries before testing. Rules can append/prepend characters, substitute characters, capitalize, multiply, or apply complex mangling. Dramatically increases wordlist coverage.

## Incremental Mode (Brute-Force)
Tries all possible character combinations in order of likelihood based on character frequency analysis. Guaranteed to succeed eventually but grows exponentially with password length.

## Pot File
A file (john.pot) where John stores successfully cracked passwords. Prevents re-cracking the same hashes across sessions. Can be inspected with `--show` or read directly.

## Hash Format Identifier
A tool that analyzes a hash string to determine its likely format. Essential for choosing the correct John mode. Common identifiers include hash-identifier and hashid.

## Unshadow
A utility that combines /etc/passwd and /etc/shadow into a format John can crack. Required for cracking Unix password hashes.
