# Snort

## Purpose
Snort is the world's most widely deployed open-source network intrusion detection and prevention system (IDS/IPS). Developed by Martin Roesch and now maintained by Cisco, Snort performs real-time traffic analysis, protocol analysis, content matching, and packet logging on IP networks. It uses a rule-driven language to detect a wide range of attacks including port scans, buffer overflows, malware C2 traffic, SQL injection, and policy violations. Snort can operate in sniffer, packet logger, or full NIDS mode.

## Installation
```bash
# Debian/Ubuntu
sudo apt update && sudo apt install snort

# Kali Linux (pre-installed)

# Red Hat/CentOS
sudo dnf install snort

# Build from source (recommended for latest version)
wget https://www.snort.org/downloads/snort/snort-2.9.20.tar.gz
tar -xzf snort-2.9.20.tar.gz
cd snort-2.9.20
./configure --enable-sourcefire
make
sudo make install

# Snort 3 (next generation)
wget https://github.com/snort3/snort3/archive/refs/tags/3.1.80.0.tar.gz
tar -xzf 3.1.80.0.tar.gz
cd snort3-3.1.80.0
./configure_cmake.sh
cd build
make -j$(nproc)
sudo make install
```

## Basic Usage
```bash
# Sniffer mode (display packets on console)
sudo snort -v
sudo snort -vd  # Verbose with data payload
sudo snort -vde # Verbose with data and link-layer headers

# Packet logger mode
sudo snort -l /var/log/snort

# NIDS mode (with rules)
sudo snort -c /etc/snort/snort.conf -i eth0

# NIDS mode with logging
sudo snort -c /etc/snort/snort.conf -l /var/log/snort -i eth0 -A console

# IPS mode (inline)
sudo snort -Q -c /etc/snort/snort.conf -i eth0:eth1
```

## Important Options
- `-v` - verbose output (show packets on console)
- `-d` - dump application layer data
- `-e` - display link-layer headers
- `-l <dir>` - log packets to specified directory
- `-c <conf>` - configuration file path
- `-i <iface>` - network interface to listen on
- `-A <mode>` - alert mode: `console`, `cmg`, `fast`, `full`, `none`, `unsock`
- `-b` - log packets in tcpdump format (binary)
- `-h <net>` - home network (e.g., `-h 10.10.10.0/24`)
- `-n <count>` - stop after processing `<count>` packets
- `-D` - run Snort in daemon (background) mode
- `-Q` - inline mode (requires appropriate network setup)
- `-T` - test and verify configuration
- `--pid-path=<path>` - PID file location
- `-U` - use UTC timestamps

## Rule Structure
Snort rules follow a specific syntax:
```
alert tcp $HOME_NET any -> $EXTERNAL_NET $HTTP_PORTS
(msg:"SQL Injection Attempt"; flow:to_server,established;
content:"union"; nocase; http_uri;
content:"select"; nocase; http_uri;
sid:1000001; rev:1;)
```

Rule components:
- **Action**: alert, log, pass, activate, dynamic, drop, reject, sdrop
- **Protocol**: tcp, udp, icmp, ip
- **Source/Destination**: IP addresses and port numbers
- **Direction**: `->`, `<>` (bidirectional)
- **Rule Options**: msg, content, sid, rev, classtype, priority, reference

## Typical Workflow
1. Install Snort and configure the main config file (`snort.conf`)
2. Define HOME_NET and EXTERNAL_NET variables
3. Configure rule paths and include appropriate rule categories
4. Test configuration: `sudo snort -T -c /etc/snort/snort.conf`
5. Start Snort in NIDS mode: `sudo snort -c /etc/snort/snort.conf -i eth0 -A console`
6. Monitor alerts in real-time or review logs in `/var/log/snort/`
7. Tune rules by commenting out noisy rules or adjusting thresholds
8. Add custom rules for organization-specific threat intelligence
9. Update community and registered rule sets regularly (pullpork or oinkmaster)
10. For IPS deployment, configure inline mode with `-Q` flag

## Advantages
- Free and open-source with extensive community support
- Highly flexible rule language for custom detection logic
- Supports multiple operating modes (sniffer, logger, NIDS, IPS)
- Large rule set (community, registered, subscriber from Talos)
- Protocol-aware inspection (HTTP, FTP, SMTP, DNS, etc.)
- Active development by Cisco Talos (industry-leading threat intelligence)
- Cross-platform (Linux, Windows, BSD, macOS)
- Can be integrated with tools like Barnyard2, BASE, and PulledPork

## Limitations
- Rule-based detection cannot identify zero-day attacks
- Performance degrades significantly with large rule sets on high-throughput links
- Requires careful tuning to reduce false positives
- No built-in protocol decryption (cannot inspect encrypted traffic)
- Snort 2.x is single-threaded (Snort 3 adds multi-threading)
- Complex configuration with many interdependent settings
- Regular rule updates needed to maintain effectiveness

## Industry Use
Snort is used by SOCs as a network monitoring sensor, by MSSPs providing managed detection services, by small-to-medium organizations as a cost-effective IDS solution, by educational institutions for teaching intrusion detection concepts, and by security researchers testing detection rule effectiveness.

## Official Documentation
- Official Site: https://www.snort.org
- Documentation: https://www.snort.org/documents
- Rule Writing Guide: https://www.snort.org/documents/snort-users-manual
- Rule Downloads: https://www.snort.org/downloads
- Talos Intelligence: https://talosintelligence.com
- GitHub: https://github.com/snort3/snort3
