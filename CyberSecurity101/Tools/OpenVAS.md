# OpenVAS (Open Vulnerability Assessment System)

## Purpose
OpenVAS is a full-featured open-source vulnerability scanner maintained by Greenbone Networks as part of the Greenbone Vulnerability Management (GVM) framework. It performs comprehensive vulnerability assessments by scanning networks, operating systems, and applications for known vulnerabilities, misconfigurations, and compliance issues. OpenVAS includes a constantly updated feed of over 100,000 Network Vulnerability Tests (NVTs) covering a wide range of CVEs, OVAL definitions, and security advisories.

## Installation
```bash
# Debian/Ubuntu (Greenbone Community Edition)
sudo apt update && sudo apt install gvm

# Initialize GVM (Greenbone Vulnerability Manager)
sudo gvm-setup

# Start services
sudo gvm-start

# Check installation
sudo gvm-check-setup

# Greenbone Security Assistant web interface
# Access at: https://127.0.0.1:9392

# Docker installation
docker pull greenbone/gvm
docker run -d -p 9392:9392 --name gvm greenbone/gvm

# Kali Linux
sudo apt update && sudo apt install openvas
sudo gvm-setup
```

## Basic Usage
Access the Greenbone Security Assistant (GSA) web interface at `https://localhost:9392`. Default credentials are generated during setup (displayed with `sudo gvm-check-setup`).

```bash
# CLI scanning using gvm-cli
gvm-cli --gmp-username admin --gmp-password <password> socket --xml '<create_target/>'

# Run a scan from command line
gvm-cli --gmp-username admin --gmp-password password socket \
  --xml='<start_task task_id="<task-id>"/>'

# Sync NVTs manually
sudo greenbone-nvt-sync
```

## Key Components
- **Greenbone Security Assistant (GSA)** - Web-based user interface
- **Greenbone Vulnerability Manager (GVM)** - Central service managing scan configs, targets, and results
- **OpenVAS Scanner** - The actual scanning engine executing NVT tests
- **NVT Feed** - Database of vulnerability tests updated by Greenbone
- **OSP (Open Scanner Protocol)** - Protocol for integrating third-party scanners
- **GPG (Greenbone Protocol)** - Communication protocol between components

## Scan Configuration Options
- **Full and fast** - Default, comprehensive scan (family-based selection)
- **Full and deep** - More thorough but slower (includes individual NVT selection)
- **Base** - Minimal scan (basic discovery and common vulns)
- **Discovery** - Host and service discovery only
- **Host Discovery** - Ping sweep and port detection
- **System Discovery** - OS fingerprinting and detailed service version detection
- **CVE Database** - Scan based on specific CVE criteria
- **Custom** - User-defined NVT selection and config

## Typical Workflow
1. Access GSA web interface and log in with admin credentials
2. Create a new target with IP address range or individual hosts
3. Verify target credentials are correct (SSH, SMB, SNMP for authenticated scanning)
4. Select a scan configuration (start with "Full and fast" for initial assessment)
5. Configure scan parameters (port range, concurrency, timeouts)
6. Launch the scan task and monitor progress
7. Review results after scan completion (severity levels: Critical, High, Medium, Low)
8. Filter and group results by severity, host, or vulnerability type
9. Export reports in various formats (PDF, HTML, XML, CSV, LaTeX)
10. Create remediation tickets or apply patches based on findings
11. Schedule recurring scans for continuous vulnerability management

## Advantages
- Completely free and open-source with no feature limitations
- Large, actively maintained NVT feed (100,000+ vulnerability tests)
- Supports authenticated scanning for deeper assessment
- Highly configurable scan policies and schedules
- Comprehensive reporting with severity ratings and remediation advice
- Centralized management through GSA web interface
- Role-based access control for multi-user environments
- Integration with external tools via OSP protocol
- Active community and commercial support available (Greenbone)

## Limitations
- Complex installation and configuration (multiple services, database setup)
- Resource intensive during scans (CPU, RAM, network bandwidth)
- Can take hours to scan large networks comprehensively
- Web interface can be slow, especially with large result sets
- False positives require manual verification
- NVT feed updates can break compatibility between components
- Some NVTs may cause service disruption (DoS-like behavior)
- Requires dedicated server for production deployment

## Industry Use
OpenVAS is used by security teams for regular vulnerability scanning, by small-to-medium businesses as a cost-effective scanning solution, by MSSPs for client assessments, by compliance auditors for regulatory scanning requirements (PCI DSS, HIPAA), and by penetration testers for initial network reconnaissance.

## Official Documentation
- Official Site: https://www.greenbone.net
- Greenbone Community Edition: https://greenbone.github.io/docs/
- Documentation: https://docs.greenbone.net
- NVT Feed: https://www.greenbone.net/en/feed/
- GitHub: https://github.com/greenbone
- OpenVAS on Kali: https://www.kali.org/tools/openvas/
