# ntopng Traffic Dashboard

## Objective

The objective of this task was to deploy ntopng and use its web-based dashboard to monitor network traffic on the Host-Only interface (`eth1`).

## Lab Environment

- Network: 192.168.56.0/24
- Monitoring Interface: eth1
- Analyst Machine: Kali Linux (192.168.56.101)
- Tool: ntopng
- Deployment Method: Docker

## Methodology

ntopng was deployed on the Kali analyst machine and configured to monitor the Host-Only network interface (`eth1`). The ntopng web dashboard was accessed to observe network traffic and identify the most active network talkers and protocols.

The dashboard was used to provide a visual overview of network activity and traffic patterns within the isolated lab environment.

## Evidence

### Figure 1 — Top Network Talkers

![ntopng top talkers](../Screenshots/Q09-ntopng/ntopng-top-talkers.png)

**Caption:** ntopng dashboard showing the top network talkers detected on the Host-Only interface (`eth1`).

### Figure 2 — Top Network Protocols

![ntopng top protocols](../Screenshots/Q09-ntopng/ntopng-top-protocols.png)

**Caption:** ntopng dashboard showing the top network protocols detected on the Host-Only interface (`eth1`).

## Results

The ntopng dashboard successfully provided a visual representation of network activity on the Host-Only interface. The dashboard displayed the most active network talkers and the protocols observed in the monitored traffic.

This provided a centralized view of network activity that can help analysts identify unusual traffic patterns, highly active hosts, and unexpected protocols.

## Skills Demonstrated

- ntopng deployment
- Network traffic monitoring
- Web-based network dashboard analysis
- Top talker identification
- Protocol analysis
- Network visibility and monitoring

## Key Learning

This task demonstrated how ntopng can provide real-time visibility into network traffic through a web-based dashboard. Monitoring top talkers and protocols can help network defenders understand normal network activity and identify potentially unusual or unexpected traffic.