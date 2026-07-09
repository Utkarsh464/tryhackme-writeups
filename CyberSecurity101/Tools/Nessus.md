# Nessus

## Purpose
Nessus is a proprietary vulnerability scanner developed by Tenable Network Security. It is one of the most widely used vulnerability assessment tools in the enterprise, capable of identifying vulnerabilities, misconfigurations, missing patches, and compliance issues across networks, operating systems, databases, web applications, and cloud environments. Nessus Professional is the industry standard for vulnerability scanning, while Nessus Essentials offers a free tier for home users and students.

## Installation
```bash
# Download Nessus from Tenable
# Requires free registration at https://tenable.com/products/nessus/nessus-essentials

# Debian/Ubuntu
wget https://www.tenable.com/downloads/api/v2/pages/nessus/files/Nessus-10.7.3-ubuntu1404_amd64.deb
sudo dpkg -i Nessus-10.7.3-ubuntu1404_amd64.deb

# Red Hat/CentOS
sudo rpm -ivh Nessus-10.7.3-es8.x86_64.rpm

# Start Nessus service
sudo /bin/systemctl start nessusd.service

# Access web interface
# https://localhost:8834

# macOS
# Download .dmg from Tenable website and install
sudo launchctl load /Library/LaunchDaemons/com.tenablesecurity.nessusd.plist
```

## Key Features
- **Asset Discovery** - Network discovery and classification of devices
- **Vulnerability Scanning** - Comprehensive scan of 100,000+ known vulnerabilities
- **Configuration Auditing** - CIS benchmarks, DISA STIGs, PCI DSS, HIPAA, SOX
- **Web Application Scanning** - SQLi, XSS, and other web vulnerabilities
- **Malware Detection** - Backdoors, Trojans, and suspicious processes
- **Patch Management Integration** - Cross-reference with missing patches
- **Compliance Scanning** - Automated compliance reporting against standards
- **Mobile Device Scanning** - iOS and Android device assessment
- **Cloud Integration** - AWS, Azure, GCP scanning capabilities

## Scan Types
- **Basic Network Scan** - Standard vulnerability scan against targets
- **Advanced Scan** - Custom scanning with full configuration options
- **Advanced Dynamic Scan** - Adaptive scanning for modern environments
- **Malware Scan** - Detect malware, backdoors, and Trojans
- **Web Application Scan** - HTTP-specific vulnerability testing
- **Mobile Device Scan** - Scan Android and iOS devices
- **Credentialed Patch Audit** - Check missing patches via authenticated access
- **Host Discovery** - Identify live hosts without vulnerability testing
- **PCI DSS Scan** - Tailored for PCI compliance requirements
- **Compliance Scan** - Benchmark against CIS, DISA, and other standards

## Typical Workflow
1. Install Nessus and register for an activation code (Essentials is free)
2. Access the web interface at `https://localhost:8834`
3. Create a new scan with the appropriate template for the target environment
4. Configure scan settings: target IPs, ports, scan intensity, time windows
5. Set up credentials for authenticated scanning (Windows: SMB/Local admin, Linux: SSH, Database: SQL auth)
6. Launch the scan and monitor progress
7. Review results sorted by severity (Critical, High, Medium, Low, Info)
8. Drill into individual findings for details: CVE references, CVSS scores, affected software, remediation guidance
9. Export reports in PDF, HTML, CSV, or Nessus format
10. Create remediation tickets or generate executive summaries for management
11. Schedule recurring scans for continuous monitoring

## Advantages
- User-friendly web interface with intuitive workflow
- Extensive plugin database (100,000+ plugins) with daily updates
- Accurate vulnerability detection with detailed remediation guidance
- Strong compliance scanning capabilities (CIS, PCI DSS, STIG)
- Authenticated scanning for deep OS and application-level assessment
- Agent-based scanning for air-gapped or mobile environments
- Integration with patch management systems (WSUS, SCCM)
- Predictive prioritization using VPR (Vulnerability Priority Rating)
- REST API for automation and orchestration

## Limitations
- Commercial licensing is expensive (Nessus Pro is $4,400/year per scanner)
- Free Nessus Essentials is limited to 16 IP addresses
- Requires activation code (internet connectivity for initial activation)
- Resource intensive on the scanning host (CPU, RAM, disk space)
- Can generate significant network traffic during scans
- False positives require manual verification and tuning
- No built-in false positive management workflow
- Learning curve for advanced configuration and tuning

## Industry Use
Nessus is the most widely deployed vulnerability scanner in the enterprise. Used by Fortune 500 companies for vulnerability management programs, by MSSPs for client scanning services, by compliance officers for audit preparation, by IT operations for patch management prioritization, and by penetration testers for initial reconnaissance.

## Official Documentation
- Official Site: https://www.tenable.com/products/nessus
- Documentation: https://docs.tenable.com/nessus/
- Plugin Database: https://www.tenable.com/plugins
- Nessus Essentials: https://www.tenable.com/products/nessus/nessus-essentials
- Training: https://www.tenable.com/education
- Community: https://community.tenable.com
