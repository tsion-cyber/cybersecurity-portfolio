# Network Threat Monitoring & Practical Traffic Analysis Lab

## Cybersecurity Portfolio Project

**Analyst:** Tsion Andarge
**Lab:** Week 2 - Networking & Traffic Monitoring
**Platform:** Oracle VirtualBox
**Primary OS:** Kali Linux
**Lab Network:** 192.168.56.0/24

## Project Overview

This project documents a hands-on cybersecurity lab focused on network threat monitoring, traffic capture, packet analysis, and practical network investigation.

The lab was conducted in an isolated VirtualBox Host-Only network using Kali Linux, Metasploitable2, pfSense, and a Docker-based DVWA web application.

The project demonstrates practical use of cybersecurity tools to perform network discovery, traffic monitoring, packet capture, HTTP object extraction, session reconstruction, and Indicator of Compromise (IOC) identification.

## Learning Objectives

* Map and inventory an isolated lab network.
* Identify hosts, open ports, and network services.
* Capture and analyze network traffic.
* Monitor network activity using Zeek and ntopng.
* Detect Nmap SYN scan traffic.
* Create and apply Wireshark display filters.
* Extract HTTP objects from packet captures.
* Analyze PCAP files using NetworkMiner.
* Reconstruct suspicious network sessions using TCP stream analysis.
* Identify and document Indicators of Compromise (IOCs).

## Lab Environment

| Role            | Hostname        | IP Address      | Platform             |
| --------------- | --------------- | --------------- | -------------------- |
| Analyst Machine | Kali            | 192.168.56.101  | Kali Linux           |
| Target Machine  | Metasploitable2 | 192.168.56.102  | Linux                |
| Firewall        | pfSense         | 192.168.56.1    | pfSense              |
| Web Application | DVWA            | 127.0.0.1:80    | Docker               |
| Lab Network     |   -              | 192.168.56.0/24 | VirtualBox Host-Only |


## Tools Used

| Tool         | Purpose                                  |
| ------------ | ---------------------------------------- |
| Nmap         | Host discovery and service enumeration   |
| Wireshark    | Packet capture and traffic analysis      |
| tcpdump      | Command-line packet capture              |
| TShark       | Command-line packet analysis             |
| Zeek         | Network monitoring and log generation    |
| ntopng       | Live network traffic monitoring          |
| NetworkMiner | PCAP artifact and credential extraction  |
| Docker       | DVWA deployment and container management |

## Lab Exercises

### Part 1 - Networking & Traffic Monitoring

| Question | Exercise                               | Result                                                |
| -------- | -------------------------------------- | ----------------------------------------------------- |
| Q6       | Nmap Host and Service Inventory        | Hosts, ports, services, and OS information identified |
| Q7       | Zeek Network Monitoring                | `conn.log` and `http.log` generated                   |
| Q8       | Traffic Capture and Nmap Scan Analysis | Nmap SYN scan signature identified                    |
| Q9       | ntopng Traffic Dashboard               | Top talkers and protocols monitored                   |
| Q10      | Wireshark Display Filters              | Host, HTTP, and SYN traffic isolated                  |

### Part 2 - Practical Traffic Analysis

| Question | Exercise                   | Result                                                    |
| -------- | -------------------------- | --------------------------------------------------------- |
| Q11      | DVWA Traffic Capture       | `dvwa_capture.pcap` created                               |
| Q12      | HTTP Object Extraction     | HTTP objects extracted from PCAP                          |
| Q13      | NetworkMiner PCAP Analysis | Hosts, files, and credentials analyzed                    |
| Q14      | TCP Stream Analysis        | Suspicious HTTP session reconstructed                     |

## Key Technical Findings

### Network Discovery

Nmap was used to scan the isolated `192.168.56.0/24` network and identify available hosts, open ports, running services, and operating system information.
The resulting host and service inventory was saved for further analysis and documentation.

### Network Monitoring

Zeek was used to monitor network traffic and generate connection and HTTP logs. ntopng was used to visualize network activity, including top network talkers and network protocols.

### Nmap SYN Scan Detection
tcpdump was used to capture traffic during an Nmap SYN scan. Wireshark was then used to identify the scan signature using the following display filter:

text
tcp.flags.syn==1 && tcp.flags.ack==0
This filter isolates TCP SYN packets without the ACK flag and was used to identify the Nmap SYN scan traffic signature.

### Wireshark Traffic Filtering
The following Wireshark display filters were used during the analysis.

**Host Traffic:**
text
ip.addr == 192.168.56.102
Used to isolate all traffic to and from the Metasploitable2 host.

**HTTP Traffic:**
text
http
Used to isolate HTTP traffic captured during the lab.

**TCP SYN Scan Traffic:**
text
tcp.flags.syn == 1 && tcp.flags.ack == 0
Used to identify TCP SYN packets without the ACK flag.

### DVWA Traffic Capture

A Docker-based DVWA web application was used to generate web application traffic. Traffic generated during login and browsing activity was captured and saved as `dvwa_capture.pcap`.

### HTTP Object Extraction

Wireshark's **File > Export Objects > HTTP** feature was used to identify and extract HTTP objects from the DVWA packet capture.

The extracted objects included:

* `brute`
* `xss_s`

### NetworkMiner Analysis

An educational training PCAP was analyzed using NetworkMiner. The analysis identified network hosts, files, and credential-related information present in the captured traffic.

### TCP Stream Analysis

Wireshark's **Follow TCP Stream** feature was used to reconstruct a suspicious HTTP communication session.

The analyzed stream did not contain observable plaintext credentials.

### IOC Analysis

The investigation documented observed network indicators including:

* IP addresses
* Domains
* User-agent strings
* File hash availability

The identified indicators were documented as observed artifacts and require additional validation before being classified as malicious.

## Project Structure
text
Network-Threat-Monitoring-Lab/
- Documentation/
- Evidence/
- Reports/
- Screenshots/
- README.md

The `Documentation` folder contains Markdown documentation for the individual lab questions.

The `Evidence` folder contains technical artifacts such as packet captures, logs, extracted HTTP objects, and the Nmap inventory.

The `Reports` folder contains the complete Week 2 Cybersecurity Lab Findings Report.

The `Screenshots` folder contains screenshots supporting the lab exercises and findings.


## Skills Demonstrated

* Network reconnaissance and discovery
* Service enumeration
* Packet capture and analysis
* Network traffic monitoring
* Nmap scan detection
* Wireshark display filtering
* TCP flag analysis
* Zeek network monitoring
* ntopng traffic visualization
* HTTP object extraction
* PCAP analysis
* NetworkMiner artifact extraction
* TCP stream reconstruction
* IOC identification and documentation


## Conclusion
This project demonstrates practical cybersecurity skills in network monitoring and traffic analysis within an isolated lab environment.

The exercises provided hands-on experience with network discovery, packet capture, traffic monitoring, reconnaissance detection, HTTP object extraction, PCAP investigation, TCP session reconstruction, and IOC documentation.

The project also demonstrates the ability to collect technical evidence, analyze network activity, document findings, and organize cybersecurity investigation artifacts in a structured portfolio.

## Disclaimer
All testing and analysis documented in this project were performed in an isolated cybersecurity lab environment using systems owned or controlled for educational purposes.
No unauthorized systems or networks were targeted.
