# tar

**Tape Archive** — a command-line utility for collecting many files into a single archive file, commonly used with compression.

## Syntax

```
tar [options] <archive-file> [files/directories]
```

## Purpose

Create, extract, and manage archive files. Often combined with gzip (`tar.gz` / `.tgz`), bzip2 (`tar.bz2`), or xz (`tar.xz`) compression. The standard archiving tool on Linux systems, used for backups, software distribution, and file transfer.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-c` | Create a new archive |
| `-x` | Extract files from an archive |
| `-t` | List contents of an archive |
| `-f <file>` | Specify archive filename |
| `-v` | Verbose (list files being processed) |
| `-z` | Compress with gzip |
| `-j` | Compress with bzip2 |
| `-J` | Compress with xz |
| `--exclude=<pattern>` | Exclude files matching pattern |
| `-C <dir>` | Change to directory before operating |
| `-r` | Append files to existing archive |
| `-u` | Update (append newer files only) |
| `-p` | Preserve permissions |
| `--strip-components=N` | Strip N leading components from paths |
| `--one-file-system` | Do not cross filesystem boundaries |

## Examples

```bash
# Create a gzip-compressed archive
tar -czvf archive.tar.gz /path/to/directory

# Create an uncompressed archive
tar -cvf archive.tar /path/to/directory

# Extract an archive
tar -xzvf archive.tar.gz

# Extract to a specific directory
tar -xzvf archive.tar.gz -C /target/directory

# List contents without extracting
tar -tzvf archive.tar.gz

# Create archive excluding certain files
tar -czvf backup.tar.gz /home/user --exclude="*.mp4" --exclude="node_modules"

# Extract with path stripping (remove top-level directory)
tar -xzvf archive.tar.gz --strip-components=1

# Create bzip2 compressed archive
tar -cjvf archive.tar.bz2 /path/to/directory

# Create xz compressed archive
tar -cJvf archive.tar.xz /path/to/directory

# Append a file to existing archive
tar -rvf archive.tar newfile.txt

# Create archive preserving permissions and ownership
tar -czvpf backup.tar.gz /etc
```

## Common Compression Ratios

| Format | Command | Typical Ratio | Speed |
|--------|---------|---------------|-------|
| `.tar` | none | 1:1 | Fastest |
| `.tar.gz` / `.tgz` | `-z` | ~2-5:1 | Fast |
| `.tar.bz2` | `-j` | ~3-7:1 | Medium |
| `.tar.xz` | `-J` | ~5-10:1 | Slow |

## Common Mistakes

- Forgetting `-f` when specifying a file — without `-f`, tar uses tape device (`/dev/rmt0`) by default.
- Not using `-z`, `-j`, or `-J` for compressed files — tar cannot detect compression automatically from the filename.
- Overwriting existing archives — using `-c` on an existing file silently overwrites it.
- Extracting without checking contents first — destructure into current directory unexpectedly.
- Using absolute paths in archives — `tar -czvf archive.tar.gz /home/user` restores files to same absolute path.
- Not using `--strip-components` when extracting an archive with a single top-level directory — creates unnecessary nesting.

## Real-World Usage

- **Backups:** Create compressed backups of configuration directories, user data, or databases.
- **Software distribution:** Most Linux source code is distributed as `.tar.gz` or `.tar.xz`.
- **CTF challenges:** Extract flag archives, unpack misconfigured backups, analyze tar files for hidden data.
- **Data transfer:** Bundle multiple files into one for efficient transfer over networks.
- **Log archiving:** Compress and rotate old log files for long-term storage.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (GNU tar) |
| Windows | Limited | Via WSL or 7-Zip |
| macOS | Full | Pre-installed (BSD tar) |

```bash
# tar is pre-installed on Linux/macOS
# Install on Linux if missing
sudo apt install tar
```
