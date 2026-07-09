# John the Ripper: The Basics — Commands

| Command | Description |
|---------|-------------|
| `john hash.txt` | Crack hashes with default settings (auto-detect, wordlist) |
| `john --list=formats` | List all supported hash formats |
| `john --wordlist=/path/wordlist.txt hash.txt` | Dictionary attack with a custom wordlist |
| `john --rules hash.txt` | Apply default rules to the wordlist |
| `john --rules=best64 hash.txt` | Apply the 64 best rules |
| `john --incremental hash.txt` | Brute-force with incremental mode |
| `john --incremental=LowerNum hash.txt` | Incremental with lowercase letters and digits |
| `john --format=raw-md5 hash.txt` | Specify the hash format |
| `john --show hash.txt` | Show cracked passwords |
| `john --pot=my.pot hash.txt` | Specify a custom pot file (cracked password database) |
| `john --session=crack1 hash.txt` | Name the cracking session (for pausing/resuming) |
| `john --restore=crack1` | Restore a paused session |
| `unshadow /etc/passwd /etc/shadow > unshadowed.txt` | Prepare Unix password hashes for John |
| `john --format=crypt unshadowed.txt` | Crack Unix shadow file hashes |
