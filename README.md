# 🐛 Bug Bounty Discipline & Methodology

A structured guide covering the bug bounty hunting discipline: methodology pipeline, common attack methods, and recommended tools.

---

## 📋 Table of Contents

1. [What is Bug Bounty?](#what-is-bug-bounty)
2. [Methodology Pipeline](#methodology-pipeline)
3. [Attack Methods & Vulnerability Classes](#attack-methods--vulnerability-classes)
4. [Tools](#tools)
5. [Tips & Best Practices](#tips--best-practices)
6. [Resources](#resources)

---

## 🎯 What is Bug Bounty?

A **Bug Bounty Program** is a crowdsourced initiative offered by organizations that rewards individuals (security researchers / ethical hackers) for responsibly reporting security vulnerabilities. Platforms such as [HackerOne](https://hackerone.com), [Bugcrowd](https://bugcrowd.com), and [Intigriti](https://intigriti.com) host thousands of programs across all industries.

---

## 🔄 Methodology Pipeline

Follow these phases in order to maximize coverage and efficiency:

### 1. Reconnaissance (Recon)
- Identify the scope (in-scope domains, IPs, endpoints)
- Enumerate subdomains
- Discover open ports and running services
- Collect email addresses, employee names, technologies used
- Map the attack surface

### 2. Scanning & Enumeration
- Active scanning of discovered hosts
- Directory and file brute-forcing
- Parameter discovery
- Technology fingerprinting (CMS, frameworks, libraries)
- JavaScript file analysis for exposed endpoints/secrets

### 3. Vulnerability Discovery
- Test each endpoint for common vulnerabilities (see [Attack Methods](#attack-methods--vulnerability-classes))
- Review JavaScript source for sensitive data
- Check for misconfigurations in cloud assets (S3 buckets, GCP, Azure blobs)
- Analyze HTTP headers for security weaknesses

### 4. Exploitation & Proof of Concept (PoC)
- Verify the vulnerability is real and exploitable
- Build a minimal, non-destructive PoC
- Document the impact clearly

### 5. Reporting
- Write a clear, reproducible report:
  - **Title** – concise description of the vulnerability
  - **Severity** – CVSS score or P1–P5 rating
  - **Steps to Reproduce** – step-by-step instructions
  - **Impact** – what an attacker could achieve
  - **Recommendations** – suggested fix
- Submit through the program's proper reporting channel
- Respond promptly to triage questions

---

## ⚔️ Attack Methods & Vulnerability Classes

| # | Vulnerability | Description |
|---|---------------|-------------|
| 1 | **XSS** (Cross-Site Scripting) | Inject malicious scripts into web pages viewed by other users |
| 2 | **SQLi** (SQL Injection) | Manipulate database queries to extract or modify data |
| 3 | **IDOR** (Insecure Direct Object Reference) | Access objects belonging to other users by changing an identifier |
| 4 | **SSRF** (Server-Side Request Forgery) | Trick the server into making requests to internal/external resources |
| 5 | **CSRF** (Cross-Site Request Forgery) | Force authenticated users to perform unintended actions |
| 6 | **Open Redirect** | Redirect users to attacker-controlled domains via manipulated URLs |
| 7 | **XXE** (XML External Entity) | Abuse XML parsers to read local files or perform SSRF |
| 8 | **RCE** (Remote Code Execution) | Execute arbitrary commands on the target server |
| 9 | **LFI / RFI** (File Inclusion) | Include local or remote files through vulnerable parameters |
| 10 | **Authentication Bypass** | Circumvent login mechanisms to access protected resources |
| 11 | **Business Logic Flaws** | Abuse application workflows in unintended ways |
| 12 | **Subdomain Takeover** | Claim abandoned subdomains pointing to unused cloud services |
| 13 | **Broken Access Control** | Access resources beyond intended permissions |
| 14 | **Sensitive Data Exposure** | Discover credentials, API keys, or PII in responses/source |
| 15 | **Host Header Injection** | Manipulate the Host header to poison caches or trigger SSRF |

---

## 🛠️ Tools

### Reconnaissance
| Tool | Purpose | Link |
|------|---------|-------|
| **Amass** | Subdomain enumeration & network mapping | [github.com/owasp-amass/amass](https://github.com/owasp-amass/amass) |
| **Subfinder** | Fast passive subdomain discovery | [github.com/projectdiscovery/subfinder](https://github.com/projectdiscovery/subfinder) |
| **Assetfinder** | Find domains and subdomains | [github.com/tomnomnom/assetfinder](https://github.com/tomnomnom/assetfinder) |
| **theHarvester** | OSINT for emails, names, and subdomains | [github.com/laramies/theHarvester](https://github.com/laramies/theHarvester) |
| **Shodan** | Search engine for internet-connected devices | [shodan.io](https://www.shodan.io) |

### Scanning & Enumeration
| Tool | Purpose | Link |
|------|---------|-------|
| **Nmap** | Network port scanner | [nmap.org](https://nmap.org) |
| **Masscan** | High-speed port scanner | [github.com/robertdavidgraham/masscan](https://github.com/robertdavidgraham/masscan) |
| **ffuf** | Fast web fuzzer for directories & parameters | [github.com/ffuf/ffuf](https://github.com/ffuf/ffuf) |
| **Gobuster** | Directory/file brute-forcing | [github.com/OJ/gobuster](https://github.com/OJ/gobuster) |
| **httpx** | HTTP probing and technology fingerprinting | [github.com/projectdiscovery/httpx](https://github.com/projectdiscovery/httpx) |
| **WhatWeb** | Web technology fingerprinting | [github.com/urbanadventurer/WhatWeb](https://github.com/urbanadventurer/WhatWeb) |
| **LinkFinder** | Discover endpoints in JavaScript files | [github.com/GerbenJavado/LinkFinder](https://github.com/GerbenJavado/LinkFinder) |

### Vulnerability Testing
| Tool | Purpose | Link |
|------|---------|-------|
| **Burp Suite** | Web application security testing proxy | [portswigger.net](https://portswigger.net/burp) |
| **OWASP ZAP** | Open-source web app scanner | [zaproxy.org](https://www.zaproxy.org) |
| **Nuclei** | Template-based vulnerability scanner | [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei) |
| **sqlmap** | Automated SQL injection detection & exploitation | [sqlmap.org](https://sqlmap.org) |
| **XSStrike** | Advanced XSS detection suite | [github.com/s0md3v/XSStrike](https://github.com/s0md3v/XSStrike) |
| **SSRFmap** | SSRF exploitation tool | [github.com/swisskyrepo/SSRFmap](https://github.com/swisskyrepo/SSRFmap) |

### Exploitation & PoC
| Tool | Purpose | Link |
|------|---------|-------|
| **Metasploit** | Exploitation framework | [metasploit.com](https://www.metasploit.com) |
| **CyberChef** | Data encoding/decoding and analysis | [gchq.github.io/CyberChef](https://gchq.github.io/CyberChef) |
| **jwt_tool** | Test and exploit JSON Web Tokens | [github.com/ticarpi/jwt_tool](https://github.com/ticarpi/jwt_tool) |

### Utility
| Tool | Purpose | Link |
|------|---------|-------|
| **curl / httpie** | Manual HTTP requests | Built-in / [httpie.io](https://httpie.io) |
| **jq** | JSON parsing from CLI | [stedolan.github.io/jq](https://stedolan.github.io/jq) |
| **waybackurls** | Fetch URLs from the Wayback Machine | [github.com/tomnomnom/waybackurls](https://github.com/tomnomnom/waybackurls) |
| **gau** | Get all URLs from multiple sources | [github.com/lc/gau](https://github.com/lc/gau) |
| **Notify** | Send findings to Slack/Discord/Telegram | [github.com/projectdiscovery/notify](https://github.com/projectdiscovery/notify) |

---

## 💡 Tips & Best Practices

- **Read the program scope carefully** — testing out-of-scope assets is against the rules.
- **Report responsibly** — do not exfiltrate user data or cause service disruption.
- **Automate recon, manual everything else** — automation finds the surface; manual testing finds the bugs.
- **Chain vulnerabilities** — a low-severity bug combined with another can become critical.
- **Prioritize high-impact bugs** — focus on RCE, SQLi, authentication bypass, and IDOR before low-severity issues.
- **Keep notes** — document every endpoint and test performed.
- **Stay updated** — follow security researchers on Twitter/X, read HackerOne disclosed reports, and practice on CTF platforms.

---

## 📚 Resources

- [HackerOne Hacktivity (Disclosed Reports)](https://hackerone.com/hacktivity)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security)
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)
- [HackTricks](https://book.hacktricks.xyz)
- [Bug Bounty Hunter Methodology by Jason Haddix](https://github.com/jhaddix/tbhm)

---

> **Disclaimer:** This repository is intended for educational purposes and authorized security testing only. Always obtain proper permission before testing any system. Unauthorized testing is illegal.
