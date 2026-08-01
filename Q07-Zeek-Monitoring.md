# Zeek Network Monitoring

## Objective

The objective of this task was to use Zeek to monitor network traffic on the Host-Only lab interface and generate network logs for traffic analysis.

## Lab Environment

- Network: 192.168.56.0/24
- Monitoring Interface: eth1
- Analyst Machine: Kali Linux (192.168.56.101)
- Traffic Source: Metasploitable2
- Tool: Zeek

## Methodology

Zeek was configured to monitor the Host-Only network interface (`eth1`). Traffic was generated from the Metasploitable2 machine to the Kali analyst machine to verify that Zeek could observe and record network activity.

Two types of traffic were generated:

1. ICMP traffic using ping requests.
2. HTTP traffic using a curl request to the Kali web server.

Zeek analyzed the captured network activity and generated structured log files for further investigation.

## Traffic Monitoring

### Figure 1 — Zeek Monitoring

![Zeek monitoring eth1](../Screenshots/Q07-Zeek/zeek-monitoring-eth1.png)

Zeek monitoring the Host-Only network interface (`eth1`) during traffic capture.

### Figure 2 — ICMP Traffic

![Zeek ICMP traffic](../Screenshots/Q07-Zeek/zeek-icmp-traffic.png)

Metasploitable2 generating ICMP traffic by sending ping requests to the Kali analyst machine (`192.168.56.101`) for Zeek monitoring.

### Figure 3 — HTTP Traffic

![Zeek HTTP traffic](../Screenshots/Q07-Zeek/zeek-http-traffic.png)

Metasploitable2 generating HTTP traffic by accessing the Kali web server using a `curl` request, which was captured by Zeek.

### Figure 4 — Zeek Log Files

![Zeek log files](../Screenshots/Q07-Zeek/zeek-log-files.png)

Zeek-generated log files (`conn.log` and `http.log`) created after capturing lab network traffic.

## Results

Zeek successfully monitored network activity on the Host-Only interface and recorded the generated traffic in structured log files. The experiment demonstrated that network connections and HTTP activity could be observed and recorded for subsequent security analysis.

## Skills Demonstrated

- Network traffic monitoring
- Zeek deployment and configuration
- Network interface monitoring
- ICMP traffic analysis
- HTTP traffic monitoring
- Network log analysis
- Security event investigation

## Key Learning

This task demonstrated how Zeek can be used as a network security monitoring tool to observe network activity and generate structured logs. The generated `conn.log` and `http.log` files provide valuable information that can support network visibility, troubleshooting, and security investigations.