# HTTP Object Extraction

## Objective

The objective of this task was to use Wireshark to extract HTTP objects and files from the `dvwa_capture.pcap` packet capture. This allowed HTTP objects transferred during the DVWA browsing activity to be identified and extracted for further analysis.

## Lab Environment

- Network: 192.168.56.0/24
- Analyst Machine: Kali Linux (192.168.56.101)
- DVWA: Docker web application
- Tool: Wireshark
- Packet Capture File: `dvwa_capture.pcap`
- Extracted Objects: `brute` and `XSS_S`

## HTTP Object Extraction Procedure

The `dvwa_capture.pcap` packet capture was opened in Wireshark. The **File > Export Objects > HTTP** option was used to display HTTP objects identified within the captured traffic. The available HTTP objects were reviewed, and relevant objects from the DVWA web application traffic were selected and extracted.

The extracted objects, including `brute` and `XSS_S`, were saved to the Documents folder for further examination.

## Evidence

### Figure 1 — HTTP Object List

![HTTP Object List](../Screenshots/Q12-HTTP-Object-Extraction/wireshark-http-list.PNG)

**Caption:** Wireshark HTTP Object List showing HTTP objects identified in the `dvwa_capture.pcap` packet capture.

### Figure 2 — Extracted HTTP Object

![Extracted HTTP Object](../Screenshots/Q12-HTTP-Object-Extraction/http-object-extracted-brute-xss.PNG )

**Caption:** HTTP objects successfully extracted from the DVWA packet capture and saved to the Documents folder, including `brute` and `XSS_S`.

## Results

The HTTP Object List successfully displayed HTTP objects identified in the `dvwa_capture.pcap` packet capture. The `brute` and `XSS_S` objects were successfully extracted from the captured traffic and saved to the Documents folder for further analysis.

## Skills Demonstrated

- Wireshark HTTP object extraction
- Packet capture analysis
- HTTP traffic analysis
- File and object recovery from network traffic
- Evidence extraction from PCAP files

## Key Learning

This task demonstrated how Wireshark can be used to identify and extract files and objects transferred through HTTP traffic. HTTP object extraction is useful in network investigations because analysts can recover transferred content from packet captures for further examination and analysis.