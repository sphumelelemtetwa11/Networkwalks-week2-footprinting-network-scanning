
# Penetration Testing Report

## Footprinting and Network Scanning Phases

**W2-PM-FINAL | Cybersecurity | NetworkWalks**

---

## Report Information

| Field | Details |
|---|---|
| **Pentester** | Emmanuel Bafi |
| **Program / Batch** | NetworkWalks — B082 |
| **Date** | 17 August 2026 |
| **Modules Completed** | W2-PM1 — Multiple Kali Linux Tools<br>W2-PM5 — Zenmap Scanning |
| **Authorized Targets** | `networkwalks.com`<br>Personal local area network |
| **Written Permission Confirmed** | Yes |
| **Phases Covered** | Phase 1 — Reconnaissance and Footprinting<br>Phase 2 — Scanning and Network Discovery |
| **Remaining Phases** | Phases 3–5 — In progress |

---

## 1. Liability and Ethical-Use Disclaimer

All activities documented in this report were performed only against systems for which I had written authorization or systems that I personally owned.

This report was prepared for educational and research purposes as part of an authorized cybersecurity training program. The techniques and tools described must not be used to access, scan, enumerate, disrupt, or test systems without explicit permission.

Unauthorized access and security testing may violate organizational policies and applicable laws and may result in disciplinary action, financial penalties, criminal prosecution, or other legal consequences.

The author, instructor, and NetworkWalks are not responsible for any misuse of the information contained in this report. Every user is responsible for ensuring that their activities remain within an approved scope.

---

## 2. Executive Summary

This report documents two Week 2 practical activities completed as part of the NetworkWalks Cybersecurity and Ethical Hacking internship:

1. **Web reconnaissance and footprinting** of the `networkwalks.com` domain using multiple Kali Linux tools.
2. **Local network discovery** using Zenmap on a personally owned local network.

The first activity focused on collecting publicly available information about the target domain, including domain records, DNS information, web technologies, HTTP response headers, and indications of Web Application Firewall protection.

The second activity focused on identifying the local network configuration, discovering active hosts, reviewing IP and MAC address information, and generating a network topology using Zenmap.

No exploitation, credential attacks, denial-of-service activity, or vulnerability exploitation was performed during these exercises.

---

## 3. Tools and Technologies Used

| Tool or Technology | Purpose |
|---|---|
| **Kali Linux** | Operating system used for authorized reconnaissance activities |
| **Windows** | Operating system used for local network discovery |
| **WHOIS** | Retrieves publicly available domain registration and registrar information |
| **WhatWeb** | Identifies web technologies, server software, CMS platforms, and related components |
| **nslookup** | Resolves domain names and queries DNS information |
| **curl** | Retrieves HTTP response headers and inspects web-server responses |
| ** wafw00f** | Checks for indications of Web Application Firewall technologies |
| **DNSRecon** | Enumerates selected DNS records and infrastructure details |
| **Zenmap** | Graphical interface for Nmap-based network discovery and scanning |
| **Windows Command Prompt** | Identifies local IP addressing and network-interface information |

---

## 4. Activities Performed

### 4.1 Web Footprinting and Reconnaissance

Authorized reconnaissance was performed against the `networkwalks.com` domain using the following tools:

- WHOIS
- WhatWeb
- nslookup
- curl
- wafw00f
- DNSRecon

Each tool was used for a specific information-gathering purpose. The results were reviewed to understand what information was publicly observable without attempting to exploit the target.

#### WHOIS

WHOIS was used to retrieve publicly available domain-registration information and identify relevant registrar and name-server details.

The results provided information about the domain registration and parts of the domain’s supporting infrastructure.

**Evidence:** Add the WHOIS screenshot or output here.

#### WhatWeb

WhatWeb was used to identify technologies exposed by the website.

The observed results included:

- WordPress `7.0.4`
- WP Download Manager `3.3.58`
- Additional web-server and application information

Technology identification is useful for understanding the visible attack surface and determining whether exposed components require security review.

**Evidence:** Add the WhatWeb screenshot or output here.

#### nslookup

The `nslookup` command was used to resolve the domain name and identify its associated IP address.

Observed result:

```text
192.232.216.135
