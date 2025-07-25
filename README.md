# Keklick - C2 Hunting, Reporting and Visualization Tool
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/e4e556fb-c81a-4106-a353-3e93bd0045dd" />

## Overview

Keklick is an advanced threat hunting platform designed to discover, map, and visualize command and control (C2) infrastructure. By identifying domains and IPs related to known malicious endpoints, security analysts can uncover complete C2 networks, helping to detect and mitigate malware campaigns and APT operations.

## Features
<img width="1913" height="877" alt="image" src="https://github.com/user-attachments/assets/4144735f-ac90-4581-a15d-4d40883b60b7" />

- C2 Infrastructure Discovery - Reveal domains and IPs connected to known malicious endpoints
- C2 Network Visualization - Map relationships between malicious infrastructure components
- Threat Intelligence Enrichment - Enhance findings with data from multiple intelligence sources
- Comprehensive C2 Reporting - Generate detailed PDF reports for incident response teams
- Interactive Analysis - Explore C2 networks through an intuitive graphical interface
- Multi-source Correlation - Connect data from DNS records, SSL certificates, and HTTP responses
- Advanced Filtering - Identify suspicious infrastructure by status codes and other attributes

## Installation Guide

### System Requirements

- Docker and Docker Compose
- Python 3.9+ (if running without Docker)
- Go 1.21+ (if running without Docker)
- Minimum 2GB RAM
- 4GB+ free disk space

### Installation Methods

#### Option 1: Using Docker (Recommended)

1. Clone the repository:
```bash
git clone https://github.com/0x6rss/keklick.git
cd keklick
```

2. Build and run the Docker container:
```bash
-docker build -t keklick .
-docker run -p 5000:5000 keklick
```

3. Access the web interface at: http://localhost:5000

#### Option 2: Manual Installation

1. Clone the repository:
```bash
git clone https://github.com/0x6rss/keklick.git
cd keklick
```

2. Install Go (version 1.21 or later):
```bash
wget https://golang.org/dl/go1.21.0.linux-amd64.tar.gz
tar -C /usr/local -xzf go1.21.0.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
```

3. Install httpx:
```bash
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
```

4. Install HEDnsExtractor:
```bash
git clone https://github.com/HuntDownProject/HEDnsExtractor.git
cd HEDnsExtractor
make
cp hednsextractor /usr/local/bin/
chmod +x /usr/local/bin/hednsextractor
cd ..
```
5. Install Python dependencies:
```bash
pip install -r requirements.txt
```
6. Run the application:
```bash
python app.py
```

7. Access the web interface at: http://localhost:5000

## Configuration

### API Keys (Optional)

Keklick uses several external APIs for enhanced C2 detection. Add your API keys to improve hunting capabilities:

1. Open app.py
2. Locate the API_KEYS dictionary
3. Replace the placeholder values with your actual API keys:
API_KEYS = {
    "abuseipdb": "your_abuseipdb_api_key",
    "otx": "your_alienvault_otx_api_key"
}

## Core Technology

Keklick leverages powerful open-source tools for efficient and comprehensive C2 infrastructure discovery:

### httpx
Keklick extensively uses httpx by ProjectDiscovery for probing potential C2 servers. This fast and multi-purpose HTTP toolkit allows for collecting detailed information about web servers, including status codes, redirects, and technologies in use - often revealing patterns consistent with C2 infrastructure.

### HEDnsExtractor
HEDnsExtractor serves as a critical backend component for C2 infrastructure discovery. This tool enables Keklick to discover hidden domain names associated with known malicious IP addresses, helping to uncover entire C2 networks that might otherwise remain hidden.

Both tools form the backbone of Keklick's C2 hunting capabilities, enabling security teams to rapidly map out malicious infrastructure networks.

## Integrations

Kecklick integrates with several external services to enhance C2 hunting:

- AbuseIPDB - Check reputation data for suspicious IP addresses
- AlienVault OTX - Gather threat intelligence on potential C2 infrastructure
- VirusTotal - Verify malicious status across multiple security vendors
- Shodan - Identify additional services and vulnerabilities on C2 servers
- Censys - Discover related malicious infrastructure components
- FOFA - Find similar C2 servers and infrastructure
- URLScan.io - Analyze suspicious domains for C2 indicators and behavior

## Usage for C2 Hunting

1. Enter a known or suspected C2 domain or IP address in the search box
2. Select the search type (Auto Detect, IP, or Domain)
3. Set the result limit based on your investigation scope
4. Click the search button to begin hunting
5. Explore the visualization of the C2 infrastructure network
6. Use the tools in the options menu for deeper analysis:
   - Threat Intelligence to verify malicious status
   - SSL Certificate Analysis to find related domains via certificates
   - DNS Records to discover additional infrastructure
   - WHOIS Information to identify ownership patterns
   - Timeline for understanding infrastructure evolution
7. Generate a comprehensive C2 infrastructure report using the Report button


## Acknowledgments

Special thanks to:
- The ProjectDiscovery team for creating httpx (https://github.com/projectdiscovery/httpx)
- The HuntDownProject team for developing HEDnsExtractor (https://github.com/HuntDownProject/HEDnsExtractor)
- All the open-source projects and APIs that make Keklick possible

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Disclaimer

Keklick is intended for legitimate security research and threat hunting purposes only. Always ensure you have proper authorization before scanning any systems or infrastructure. The developers take no responsibility for misuse of this tool.
