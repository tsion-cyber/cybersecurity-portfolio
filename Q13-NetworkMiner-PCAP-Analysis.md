# NetworkMiner PCAP Analysis

## Objective

The objective of this task was to download a training PCAP file from malware-traffic-analysis.net and use NetworkMiner to automatically extract and analyze hosts, files, and credential information from the captured network traffic.

## Lab Environment

- Network: 192.168.56.0/24
- Analyst Machine: Kali Linux (192.168.56.101)
- Tool: NetworkMiner
- PCAP Source: malware-traffic-analysis.net
- Analysis File: Training PCAP file

## NetworkMiner Analysis Procedure

A training exercise PCAP file was downloaded from malware-traffic-analysis.net, an educational resource containing purpose-built network traffic analysis exercises. The PCAP file was opened in NetworkMiner to automatically analyze the captured network traffic.

The **Hosts** tab was used to identify hosts and IP addresses observed in the PCAP. The **Files** tab was examined to identify files automatically extracted from the captured traffic. The **Credentials** tab was reviewed to identify credential information present in the training PCAP.

## Evidence

### Figure 1 — NetworkMiner Hosts Tab

![NetworkMiner Hosts Tab](../Screenshots/Q13-NetworkMiner-PCAP-Analysis/networkminer-hosts-tab.png)

**Caption:** NetworkMiner Hosts tab showing hosts and IP addresses identified in the training PCAP file.

### Figure 2 — NetworkMiner Files Tab

![NetworkMiner Files Tab](../Screenshots/Q13-NetworkMiner-PCAP-Analysis/networkminer-files-tab.png)

**Caption:** Files tab showing files automatically extracted from the training PCAP file.

### Figure 3 — NetworkMiner Credentials Tab

![NetworkMiner Credentials Tab](../Screenshots/Q13-NetworkMiner-PCAP-Analysis/networkminer-credentials-tab.png)

**Caption:** NetworkMiner Credentials tab showing credential information identified in the training PCAP file.

## Results

NetworkMiner successfully analyzed the training PCAP file and automatically identified hosts and IP addresses observed in the captured traffic. The tool also extracted files and identified credential information from the network traffic. The results demonstrated how NetworkMiner can automate the extraction of useful artifacts from packet capture files.

## Skills Demonstrated

- NetworkMiner PCAP analysis
- Host and IP address identification
- Automatic file extraction
- Credential artifact identification
- Network traffic investigation
- PCAP-based forensic analysis

## Key Learning

This task demonstrated how NetworkMiner can automatically extract valuable network artifacts from a PCAP file. The Hosts, Files, and Credentials tabs provide investigators with a quick way to identify systems, recover transferred files, and locate credential information that may be relevant during network security investigations.