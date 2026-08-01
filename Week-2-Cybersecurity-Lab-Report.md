# QIYAS Addis Abeba University Cybersecurity Lab Findings Report

## Lab: Week 2 – Networking & Traffic Monitoring

**Week #:** Week 2  
**Analyst:** Tsion Andarge  
**Date(s) Performed:** July 21, 2026  
**Lab Host Machine:** Oracle VirtualBox (Kali Linux)  
**Reference Decks:** `Network_Threat_Monitoring.pptx` and `Network_Packet_Analysis.pptx`

---

# Part 1 — Networking & Traffic Monitoring

## 1. Objectives

- Map the isolated lab network.
- Discover hosts and running network services.
- Monitor network traffic using packet capture and network monitoring tools.
- Analyze network scan behavior.
- Practice writing Wireshark display filters.
- Identify network traffic patterns associated with reconnaissance activity.

## 2. Tools Used

| Tool | Purpose | Version / Install Notes |
|---|---|---|
| Nmap | Host and service discovery | Installed using apt |
| Wireshark | Packet capture and analysis | Installed |
| tcpdump | Command-line packet capture | Installed |
| TShark | Command-line packet analysis | Installed |
| Docker | Container platform | Installed |
| Zeek | Network monitoring | Docker image used |
| ntopng | Network traffic dashboard | Docker image used |

## 3. Environment & Targets

| Role | Hostname | IP Address | OS / Image |
|---|---|---|---|
| Analyst machine | Kali | 192.168.56.101 | Kali Linux |
| Target machine | Metasploitable2 | 192.168.56.102 | Linux |
| Firewall | pfSense | 192.168.56.1 | pfSense |
| Web Target | DVWA | 127.0.0.1:80 | Docker |
| Lab Network | — | 192.168.56.0/24 | VirtualBox Host-Only |

## 4. Methodology / Actions Performed

1. Installed the required networking and packet analysis tools.
2. Verified the available network interfaces on Kali Linux.
3. Performed host discovery and service enumeration using Nmap.
4. Captured network traffic using TShark and tcpdump.
5. Opened packet captures in Wireshark for inspection.
6. Used Zeek to monitor network traffic and generate connection and HTTP logs.
7. Used ntopng to monitor network traffic, top talkers, and protocols.
8. Created Wireshark display filters to isolate specific traffic.
9. Analyzed TCP SYN traffic associated with an Nmap SYN scan.
10. Attempted to install a Windows 10 virtual machine. The installation could not be completed because the host computer ran out of disk space, resulting in a VirtualBox `VERR_DISK_FULL` error.

## 5. Findings & Results

| # | Observation / Finding | Evidence Reference |
|---|---|---|
| 1 | Nmap successfully identified hosts, open ports, services, and operating system information in the `192.168.56.0/24` lab network. | Q6 |
| 2 | The Nmap host and service inventory was saved to `inventory.txt` for documentation and further analysis. | Q6 |
| 3 | Zeek monitored the Host-Only network interface and captured network traffic generated during the lab. | Q7 |
| 4 | Zeek successfully generated `conn.log` and `http.log` files containing connection and HTTP traffic information. | Q7 |
| 5 | tcpdump captured network traffic while an Nmap SYN scan was performed against Metasploitable2. | Q8 |
| 6 | Wireshark identified the Nmap SYN scan using the filter `tcp.flags.syn==1 && tcp.flags.ack==0`. | Q8 |
| 7 | ntopng displayed network traffic information, including top network talkers and protocols. | Q9 |
| 8 | Wireshark successfully filtered all traffic to and from the Metasploitable2 host. | Q10 |
| 9 | Wireshark successfully isolated HTTP traffic between Kali and the Metasploitable2 web server. | Q10 |
| 10 | Wireshark successfully isolated TCP SYN packets without ACK, highlighting the Nmap SYN scan traffic signature. | Q10 |

---

# Part 2 — Practical Traffic Analysis

## 6. Objectives

- Reconstruct network sessions from packet captures.
- Extract Indicators of Compromise (IOCs) from packet captures.
- Analyze files and objects transferred through HTTP traffic.
- Identify hosts, files, credentials, and other network artifacts.
- Differentiate between benign and potentially suspicious traffic patterns.

## 7. Tools Used

| Tool | Purpose | Version / Install Notes |
|---|---|---|
| Wireshark | Deep packet and session reconstruction | Installed |
| NetworkMiner | Automated artifact, file, host, and credential extraction from PCAPs | Used for training PCAP analysis |
| TShark | Command-line and scriptable packet analysis | Installed using apt |
| tcpdump | Network packet capture | Installed |
| Docker | Container platform for running DVWA | Installed |
| DVWA | Web application used to generate traffic for packet analysis | Docker image |

## 8. Environment & Targets

| Role | Hostname | IP Address | OS / Image |
|---|---|---|---|
| Analyst machine | Kali | 192.168.56.101 | Kali Linux |
| Target machine | Metasploitable2 | 192.168.56.102 | Linux |
| Firewall | pfSense | 192.168.56.1 | pfSense |
| Web Target | DVWA | 127.0.0.1:80 | Docker |
| Training PCAP | — | — | Educational training capture |

## 9. Methodology / Actions Performed

1. Deployed the DVWA web application using Docker.
2. Captured network traffic while logging in and browsing the DVWA application.
3. Saved the captured traffic as `dvwa_capture.pcap`.
4. Opened the DVWA packet capture in Wireshark.
5. Used **File > Export Objects > HTTP** to identify and extract HTTP objects.
6. Extracted the `brute` and `xss_s` HTTP objects from the captured traffic.
7. Obtained an educational training PCAP for network traffic analysis.
8. Used NetworkMiner to automatically identify hosts, files, and credential information from the training PCAP.
9. Used Wireshark's **Follow TCP Stream** feature to reconstruct a suspicious HTTP communication session.
10. Documented the source, destination, protocol, transferred files, and plaintext credentials observed.
11. Identified and summarized network indicators, including IP addresses, domains, user-agent strings, and file hash availability.

## 10. Findings & Results

| # | Observation / Finding | Evidence Reference | Notes |
|---|---|---|---|
| 1 | DVWA traffic was successfully captured and saved as `dvwa_capture.pcap`. | Q11 | Packet capture successfully created |
| 2 | HTTP objects were identified and successfully extracted from the DVWA PCAP. | Q12 | Extracted objects included `brute` and `xss_s` |
| 3 | NetworkMiner identified hosts, files, and credential information in the training PCAP. | Q13 | Security-relevant artifacts identified |
| 4 | A suspicious HTTP session was analyzed using Wireshark Follow TCP Stream. No plaintext credentials were observed in the analyzed stream. | Q14 | Suspicious traffic analyzed |
| 5 | Several IP addresses and domains were identified during the analysis. No file hash was available from the analyzed evidence. | Q15 | IOC information documented |

---

## 11. IOC Summary

The following indicators were observed during the network traffic and PCAP analysis. These values are documented as observed indicators and are not automatically classified as malicious without additional validation.

| IOC Type | IOC Value | Description |
|---|---|---|
| IP Address | `20.49.50.241` | IP address observed in the analyzed traffic and associated with a Microsoft-related domain. |
| Domain | `whitepepper.su` | Domain identified in the captured traffic. |
| Domain | `settings-prod-uks-2.uksouth.cloudapp.azure.com` | Domain identified in the captured traffic. |
| Domain | `atm-settingsfe-prod-geo2.trafficmanager.net` | Domain identified in the captured traffic. |
| Domain | `settings-win.data.microsoft.com` | Domain identified in the captured traffic. |
| User-Agent | `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 ... Chrome/144.0.0.0 Safari/537.36` | Browser user-agent string observed in HTTP traffic. |
| File Hash | `Not identified` | No file hash was available from the analyzed evidence. |

---

## 12. Evidence and Artifacts

The following technical artifacts were preserved in the project `Evidence` folder:

- `inventory.txt` — Nmap host and service inventory.
- `conn.log` — Zeek connection log.
- `http.log` — Zeek HTTP log.
- `nmap_scan.pcap` — Packet capture associated with the Nmap scan analysis.
- `dvwa_capture.pcap` — Packet capture created during DVWA login and browsing activity.
- Training PCAP — Educational traffic analysis capture used for NetworkMiner analysis.
- `brute` — HTTP object extracted from the DVWA packet capture.
- `xss_s` — HTTP object extracted from the DVWA packet capture.

---

## 13. Conclusion

The Week 2 cybersecurity lab provided practical experience in network discovery, traffic monitoring, packet capture, and network traffic analysis. Nmap was used to identify hosts and services within the isolated lab network, while Zeek and ntopng were used to monitor network activity. tcpdump and Wireshark were used to capture and analyze traffic associated with an Nmap SYN scan.

The practical traffic analysis exercises demonstrated how Wireshark can reconstruct network sessions and extract HTTP objects from packet captures. NetworkMiner was used to automatically identify hosts, files, and credential-related artifacts from a training PCAP. The analysis also demonstrated how network indicators such as IP addresses, domains, and user-agent strings can be documented for further investigation.

Overall, the exercises strengthened practical skills in network reconnaissance detection, packet analysis, HTTP object extraction, session reconstruction, and IOC identification using industry-relevant cybersecurity tools.