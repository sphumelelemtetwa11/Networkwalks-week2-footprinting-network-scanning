# Penetration Testing Report

## Footprinting and Network Scanning Phases

**W2-PM-FINAL | Cybersecurity | NetworkWalks**

---

## Report Information

| Field | Details |
|---|---|
| **Pentester** | siphumelele Mtetwa |
| **Program / Batch** | NetworkWalks — B083 |
| **Date** | 19 September 2026 |
| **Modules Completed** | W2-PM1 — Multiple Kali Linux Tools<br>W2-PM5 — Zenmap Scanning |
| **Authorized Targets** | `networkwalks.com`<br>Personal local area network |
| **Written Permission Confirmed** | Yes |
| **Phases Covered** | Phase 1 — Reconnaissance and Footprinting<br>Phase 2 — Scanning and Network Discovery |


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

<img width="1920" height="955" alt="1-whois" src="https://github.com/user-attachments/assets/dfc0de1b-9704-480c-acb9-45b1aacc89ce" />






#### WhatWeb

WhatWeb was used to identify technologies exposed by the website.

The observed results included:

- WordPress `7.1.1`
- WP Download Manager `3.3.58`
- Additional web-server and application information

Technology identification is useful for understanding the visible attack surface and determining whether exposed components require security review.


<img width="1920" height="955" alt="2-whatweb" src="https://github.com/user-attachments/assets/a0e2c9df-ecbb-4374-b178-473b2230c047" />






#### nslookup

The `nslookup` command was used to resolve the domain name and identify its associated IP address.

Observed result:

```
192.232.216.135
```


<img width="1920" height="955" alt="3-nslookup" src="https://github.com/user-attachments/assets/e415203c-4f26-473e-9437-c0af9cec9f57" />





#### curl


The following command was used to inspect the website’s HTTP response headers:


```
curl -I https://networkwalks.com

```

The response provided additional information about the web service and indicated that the WordPress REST API endpoint was available at:

```
/wp-json/

```

The presence of an endpoint does not by itself indicate a vulnerability. It should only be reviewed further within the approved testing scope.



<img width="1227" height="843" alt="ncurlnetworkwalks" src="https://github.com/user-attachments/assets/d78decd9-a3ee-46b4-9cf6-406d294db6c8" />





#### wafw00f


The `wafw00f` tool was used to check whether the website appeared to be protected by a Web Application Firewall.


The result identified an indication of:


```
ModSecurity — SpiderLabs

```


This result identifies a possible security-control technology. It does not confirm the effectiveness of the configuration or the absence of vulnerabilities.


<img width="1920" height="955" alt="5-wafw00f" src="https://github.com/user-attachments/assets/189bfafc-4bdc-4f74-a63a-beaf8ae76786" />





#### DNSRecon


DNSRecon was used to enumerate publicly available DNS records.


The results included information related to:

- Name servers

- Mail servers

- SPF and TXT records

- Service records

- DNS infrastructure



DNS records can provide useful information about an organization’s publicly visible infrastructure and should be reviewed regularly.

<img width="1920" height="955" alt="6-dnsrecon" src="https://github.com/user-attachments/assets/b1102b79-1318-4f8f-98ca-9a4f90618e9f" />




### 4.2 Local Network Discovery with Zenmap


The second practical activity involved discovering active hosts on my personally owned local network using Zenmap.


The following activities were completed:



1. Identified the local IP address and subnet using kali terminal

2. Entered the authorized subnet into Zenmap.

3. Selected a Ping Scan profile to identify active hosts.

4. Reviewed the IP and MAC address information returned by the scan.

5. Opened the Zenmap Topology view.

6. Enabled the topology legend.





The example scan identified the following live hosts:

```
10.0.0.1
10.0.0.2

```

The scan also returned MAC-address information for the discovered devices.

**Evidence:** 



<img width="1920" height="955" alt="Zenmap out" src="https://github.com/user-attachments/assets/26ad55a3-bf49-4351-8cb8-3474a0d6ce3a" />





<img width="1920" height="955" alt="Zenmap Topology" src="https://github.com/user-attachments/assets/7f6e042f-df6b-4827-a536-5b2d064c781a" />







## 5. Findings and Risk Analysis


The following observations were identified during the footprinting and network-discovery exercises.

| No. | Observation | Evidence | Security Significance | Risk |
| --- | --- | --- | --- | --- |
| 1 | Web technologies were identifiable | WhatWeb identified WordPress and WP Download Manager | Technology and version information may help prioritize further security review | Medium |
| 2 | The web-service IP address was identifiable | nslookup resolved the domain to `192.232.216.135` | The address provides information about the service’s network location | Low |
| 3 | HTTP response information was exposed | curl returned response headers and indicated `/wp-json/` | Response details may assist technology fingerprinting and authorized enumeration | Low |
| 4 | WAF technology was identifiable | wafw00f indicated ModSecurity | This reveals information about the site’s visible defensive architecture | Low |
| 5 | DNS infrastructure was publicly observable | DNSRecon identified DNS, mail, and service records | DNS data can help build a broader infrastructure profile | Medium |
| 6 | Multiple hosts were visible on the local network | Zenmap identified 2 live hosts in the network | Unknown or unauthorized devices may require investigation | Medium |



### Risk Rating Key

- **Critical:** Immediate and severe risk requiring urgent action

- **High:** Significant risk requiring timely remediation

- **Medium:** Moderate risk requiring review and appropriate mitigation

- **Low:** Limited risk or informational observation



These are observations from information-gathering and host-discovery activities. They are not confirmed vulnerabilities.


No exploitation or vulnerability validation was performed during these modules. The presence of a software version, IP address, DNS record, HTTP header, or API endpoint does not automatically indicate that a system is vulnerable. Additional authorized testing would be required to verify exploitability and business impact.



## 6. Recommendations


### 6.1 Review Publicly Exposed Technology Information


Organizations should periodically review the technologies, CMS platforms, plugins, and server information visible from the Internet.


Where possible, unnecessary version details should be minimized without affecting application functionality or troubleshooting requirements.


### 6.2 Maintain Current Software Versions


WordPress, plugins, web servers, operating systems, and supporting components should be regularly updated.


Security advisories should be monitored, and updates should be tested before deployment to production environments.


### 6.3 Review HTTP Response Headers


HTTP response headers should be reviewed to identify unnecessary technical information and confirm that appropriate security headers are configured.


### 6.4 Review DNS Records


DNS records should be reviewed periodically to ensure that only required services are publicly exposed.


Unused records should be removed, and mail, SPF, DKIM, DMARC, and service records should be maintained accurately.


### 6.5 Configure and Monitor the WAF


The Web Application Firewall should remain enabled, regularly updated, and appropriately tuned.


WAF alerts and blocked requests should be monitored to identify attack patterns and reduce false positives.


### 6.6 Perform Regular Internal Network Discovery


Organizations should periodically review their internal networks to identify active devices, unexpected services, and unauthorized systems.


Network discovery should be conducted under an approved scope and according to organizational policy.


### 6.7 Investigate Unknown Devices


Any unexpected host discovered during network scanning should be identified, verified, and investigated.


Device inventories should be maintained so that approved systems can be distinguished from unknown or unauthorized devices.


### 6.8 Maintain Network Documentation


Network diagrams, IP-address assignments, device inventories, and system ownership information should be documented and updated regularly.


### 6.9 Conduct Security Testing with Authorization


Reconnaissance and scanning must only be performed against systems and networks for which appropriate authorization has been obtained.


The approved scope, testing window, source IP addresses, permitted tools, and reporting requirements should be documented before testing begins.



## 7. Conclusion


During Week 2 of the NetworkWalks Cybersecurity and Ethical Hacking internship, I completed practical activities covering web footprinting, reconnaissance, and local network discovery.


During the footprinting exercise, I used WHOIS, WhatWeb, nslookup, curl, wafw00f, and DNSRecon to collect publicly observable information about the authorized domain. This helped me understand how security professionals identify domain details, web technologies, IP addresses, HTTP responses, WAF indicators, and DNS infrastructure.


During the network-scanning exercise, I used Windows network commands and Zenmap to identify my local network configuration and discover active hosts. I also reviewed IP and MAC address information and created a network-topology diagram.


These exercises demonstrated that information gathering is an important part of cybersecurity. Before any vulnerability validation or exploitation is attempted, a security professional can learn a significant amount about an environment by analyzing publicly available information and network responses.


I also learned the importance of clear technical reporting. A professional security report should explain:


- What activity was performed

- Which tools and commands were used

- What information was observed

- Why each observation matters

- What risks may exist

- What security improvements are recommended

- What limitations applied to the assessment



Most importantly, I learned that reconnaissance and scanning must always remain within an authorized scope. All activities documented in this report were completed as part of an approved educational cybersecurity laboratory.



## 8. Evidence Collected

<img width="1920" height="955" alt="2-whatweb" src="https://github.com/user-attachments/assets/74982801-a601-4788-b3fe-1d6cd3180d6c" />




<img width="1920" height="955" alt="Zenmap Topology" src="https://github.com/user-attachments/assets/88811bd4-4cdd-4390-9181-ea5b8d18c443" />




<img width="1920" height="955" alt="Zenmap out" src="https://github.com/user-attachments/assets/81d63177-50b2-4a48-87ba-e6fcd772f47c" />




<img width="1920" height="955" alt="Screenshot_2026-09-19_11_00_59" src="https://github.com/user-attachments/assets/3c62de56-b4cb-49a2-b53e-a80147aba429"/>




<img width="1920" height="955" alt="Screenshot_2026-09-19_10_44_17" src="https://github.com/user-attachments/assets/2812f9b2-f9b7-4e11-a1f5-758076ec4309"/>




<img width="1920" height="955" alt="6-dnsrecon" src="https://github.com/user-attachments/assets/48adaef8-1527-47be-b35f-b99a559f1d88" />




<img width="1920" height="955" alt="5-wafw00f" src="https://github.com/user-attachments/assets/e03c5ea9-d667-49b3-9c38-9d02efd44cc4" />




<img width="1920" height="955" alt="4-Curl" src="https://github.com/user-attachments/assets/0bbbdbf9-4305-4e7f-a0ad-380a76f4c093" />




<img width="1920" height="955" alt="3-nslookup" src="https://github.com/user-attachments/assets/69183662-0b13-44ae-ab36-036f9fff5d22" />




<img width="1920" height="955" alt="1-whois" src="https://github.com/user-attachments/assets/acab5f84-2f2a-40bc-a4c6-2601c4f5e118" />

