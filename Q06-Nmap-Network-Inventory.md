# Nmap Network Inventory

## Objective

The objective of this task was to discover active hosts and identify the services and operating systems running on the isolated lab network.

## Lab Network

* Network: 192.168.56.0/24
* Tool: Nmap
* Operating System: Kali Linux

## Command Used

```bash
sudo nmap -sV -O 192.168.56.0/24
```

## Methodology

I performed an Nmap scan from the Kali Linux analyst machine against the isolated `192.168.56.0/24` lab network. The scan was used to identify active hosts, detect running services and determine operating system information where possible.

## Results

The Nmap scan identified two active hosts within the `192.168.56.0/24` lab network.

### Host 1: 192.168.56.1

The host was identified as a Windows-based system with the hostname `DESKTOP-NPP9ASC`. The scan detected the following open TCP ports and services:

| Port | Service               | Detected Information                 |
| ---- | --------------------- | ------------------------------------ |
| 135  | MSRPC                 | Microsoft Windows RPC                |
| 139  | NetBIOS-SSN           | Microsoft Windows NetBIOS            |
| 445  | Microsoft-DS          | Microsoft Windows file sharing (SMB) |
| 902  | VMware Authentication | VMware Authentication Daemon         |
| 912  | VMware Auth           | VMware Authentication Daemon         |
| 3389 | MS-WBT-Server         | Microsoft Remote Desktop (RDP)       |
| 5357 | HTTP                  | Microsoft HTTPAPI 2.0                |

Nmap estimated the operating system as Microsoft Windows 10/11. However, the scan noted that the OS identification may be unreliable because the required combination of open and closed ports was not available.

### Host 2: 192.168.56.100

The second active host was identified as an Oracle VirtualBox virtual network device. All 1000 scanned TCP ports were filtered, and Nmap could not determine a specific operating system.

### Summary

The scan provided an initial inventory of active hosts, exposed services, and operating system information within the isolated lab network. This inventory can be used as a baseline for subsequent network monitoring and security analysis.

## Evidence

![Nmap Network Inventory](../Screenshots/Q06-Nmap/nmap-network-inventory.png)

## Skills Demonstrated

* Network discovery
* Nmap scanning
* Service enumeration
* Operating system detection
* Host and service inventory creation
* Network reconnaissance and baseline analysis

## Key Learning

This task demonstrated how network defenders can use Nmap to build an initial understanding of the systems and services present in a network. This information can be used as a baseline for monitoring and identifying unexpected changes.

The scan also demonstrated the importance of interpreting automated OS detection results carefully, as Nmap may provide estimated results when scan conditions are not ideal.
