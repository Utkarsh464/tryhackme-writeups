# Commands: Data Representation

## Linux Conversion Utilities

| Command | Description |
|---------|-------------|
| `bc` | Command-line calculator for base conversion |
| `printf '%x\n' 255` | Convert decimal to hexadecimal |
| `printf '%o\n' 255` | Convert decimal to octal |
| `echo 'obase=2;255' | bc` | Convert decimal to binary using bc |
| `echo 'ibase=2;11111111' | bc` | Convert binary to decimal using bc |
