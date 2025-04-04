# Digital Forensics Case Study: 17ebook.com

## Project Overview
This project examines the website `17ebook.com` using various digital forensics tools to assess its security and identify potential threats. The investigation covers multiple aspects including malware detection, network traffic analysis, DNS information, domain registration details, vulnerability assessment, and open-source intelligence gathering.

## Team Members
- VU22CSEN0400021-Shyamonth
- VU22CSEN0400030-Shriya
- VU22CSEN0400037-Charanya
- VU22CSEN0400087-Danush

## Tools Used
1. VirusTotal - For malware detection and URL analysis
2. Wireshark - For network traffic analysis
3. nslookup - For DNS record investigation
4. whois - For domain registration information
5. Metasploit (msfconsole) - For vulnerability scanning
6. Nmap - For port scanning and service detection
7. wget - For website content downloading
8. theHarvester - For OSINT information gathering

## Methodology

### 1. VirusTotal Analysis
**Purpose**: To check if the website is reported as malicious by multiple antivirus engines  
**Command**:  
Visited https://www.virustotal.com/gui/home/url and entered http://17ebook.com  
**Forensic Phase**: Incident Detection & Malware Analysis  
**Findings**:  
- The website was scanned against multiple antivirus engines
- Detection rates and domain reputation were analyzed
- Any associated malware or blacklisting was identified
- Results showed [include your actual findings here - whether it was flagged by any engines]

### 2. Wireshark Analysis
**Purpose**: To capture and analyze network traffic to/from the website  
**Command**:  
	wireshark
	Filter applied: http contains "17ebook.com"
**Forensic Phase**: Network Traffic Analysis  
**Findings**:  
- Captured all HTTP traffic containing "17ebook.com"
- Analyzed for suspicious packets, redirects, and payloads
- Extracted IP addresses, domains, and HTTP requests
- Identified potential command-and-control (C2) connections
- Found [describe your actual findings - any suspicious traffic patterns]

### 3. nslookup Analysis
**Purpose**: To query DNS records of the domain  
**Command**:  
	nslookup 17ebook.com
**Forensic Phase**: Domain & Infrastructure Investigation  
**Findings**:  
	Server: 192.168.160.65
	Address: 192.168.160.65#53

	Non-authoritative answer:
	Name: 17ebook.com
	Address: 208.91.196.152
- Identified the IP address of the website (208.91.196.152)
- Extracted A record information
- Could be extended to check MX and NS records

### 4. whois Analysis
**Purpose**: To fetch domain registration details  
**Command**:  
	whois 17ebook.com
**Forensic Phase**: Domain Profiling & Attribution  
**Findings**:  
- Retrieved domain registration details including:
  - Registrant information
  - Registrar details
  - Creation and expiration dates
  - Contact information
  - Country of registration
- [Include specific details you found from the whois lookup]

### 5. Metasploit (msfconsole) Analysis
**Purpose**: To perform vulnerability assessment  
**Command**:  
	msfconsole
	use auxiliary/scanner/http/http_version
	set RHOSTS 17ebook.com
	run
**Forensic Phase**: Vulnerability Identification  
**Findings**:  
	[+] 208.91.196.152:80 Apache (302-//ww6.17ebook.com)
- Identified server type (Apache)
- Detected HTTP version and server headers
- Found redirect to ww6.17ebook.com
- Could be extended to check for specific vulnerabilities

### 6. Nmap Analysis
**Purpose**: To scan for open ports and vulnerabilities  
**Command**:  
	nmap -sV --script=http-vuln-cve2017-5638 17ebook.com
**Forensic Phase**: Vulnerability Assessment  
**Findings**:  
	Nmap scan report for 17ebook.com (208.91.196.152)
	Host is up (0.40s latency).
	Not shown: 997 filtered tcp ports (no-response)
	PORT STATE SERVICE VERSION
	53/tcp open domain?
	80/tcp open http Apache httpd
	443/tcp open ssl/http OpenResty web app server
- Discovered open ports (53, 80, 443)
- Identified services running (Apache, OpenResty)
- Scanned for specific vulnerabilities (Apache Struts RCE)
- [Add any vulnerability findings]

### 7. wget Analysis
**Purpose**: To download website content for offline analysis  
**Commands**:  
	Download homepage
		wget -O 17ebook.html http://17ebook.com

	Download specific file (e.g., suspected malware)
		wget http://17ebook.com/malware.exe

	Mirror entire website
	wget --mirror -p --convert-links -P website_files http://17ebook.com
**Forensic Phase**: Content Analysis & Malware Investigation  
**Findings**:  
- Downloaded HTML source code for manual inspection
- Retrieved executable files for malware analysis
- Mirrored website structure for complete analysis
- Found [describe any suspicious scripts, iframes, or redirects]
- Observed 302 redirect to ww5.17ebook.com

### 8. theHarvester Analysis
**Purpose**: To gather OSINT information about the domain  
**Command**:  
	theHarvester -d 17ebook.com -b all
**Forensic Phase**: Open-Source Intelligence (OSINT)  
**Findings**:  
- Discovered multiple subdomains:
  - www1.17ebook.com
  - www2.17ebook.com
  - www5.17ebook.com
  - www6.17ebook.com
  - www7.17ebook.com
  - [and many others]
- Found 55 associated IP addresses
- Identified 17 interesting URLs related to the domain
- Collected ASN information (AS16509, AS40034, AS47846)

## Findings Summary
[Comprehensive summary of all findings across tools]
- The website resolves to IP 208.91.196.152
- Uses Apache and OpenResty web servers
- Has multiple subdomains and redirects
- [Include any malware findings]
- [Note any vulnerabilities discovered]
- [Highlight suspicious patterns observed]

## How to Reproduce
1. Install required tools:
   - Wireshark, Metasploit Framework, Nmap, theHarvester
   - Standard Linux tools: whois, nslookup, wget
2. Run commands as documented in each section
3. Compare your results with our findings
4. For GUI tools like VirusTotal, visit their websites
