# TCP Stream Analysis

## Objective

The objective of this task was to follow the TCP stream of a suspicious network session in Wireshark and document the source and destination addresses, protocol used, any transferred files, and any plaintext credentials observed in the session.

## Lab Environment

- Network: 192.168.56.0/24
- Analyst Machine: Kali Linux (192.168.56.101)
- Tool: Wireshark
- Analysis Method: Follow TCP Stream
- Protocol: HTTP

## TCP Stream Analysis Procedure

The suspicious network session was opened in Wireshark, and the **Follow > TCP Stream** option was used to reconstruct the TCP conversation. The reconstructed stream was examined to identify the source and destination systems, the protocol used, HTTP requests and server responses, any file or object transferred during the session, and any plaintext credentials visible in the communication.

The TCP stream showed an HTTP GET request and a corresponding server response. No plaintext credentials were observed in the analyzed TCP stream.

## Evidence

### Figure 1 — Wireshark Follow TCP Stream

![Wireshark Follow TCP Stream](../Screenshots/Q14-TCP-Stream-Analysis/wireshark-follow-tcp-stream.png)

**Caption:** Wireshark Follow TCP Stream showing the suspicious HTTP session, including the HTTP GET request and server response. No plaintext credentials were observed.

## Analysis Findings

| Item | Finding |
|---|---|
| Source | Kali Linux (192.168.56.101) |
| Destination | Metasploitable2 (192.168.56.102) |
| Protocol | HTTP over TCP |
| File Transferred | No file transfer identified in the analyzed TCP stream |
| Plaintext Credentials | None observed |
| Session Activity | HTTP GET request and server response |

## Results

The TCP stream was successfully reconstructed using Wireshark's Follow TCP Stream feature. The analysis identified an HTTP session between the source and destination systems and displayed the HTTP GET request and corresponding server response. No plaintext credentials or file transfers were identified in the analyzed TCP stream.

## Skills Demonstrated

- Wireshark TCP stream analysis
- TCP session reconstruction
- HTTP traffic analysis
- Source and destination identification
- Detection of plaintext credentials
- Network session investigation

## Key Learning

This task demonstrated how Wireshark's Follow TCP Stream feature can reconstruct and display an entire TCP conversation. This technique helps analysts understand the communication between systems, identify protocols and requests, examine transferred content, and determine whether sensitive information such as plaintext credentials is exposed in network traffic.