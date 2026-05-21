# Wireshark Fundamentals

---

# Project Overview

This report documents a network traffic analysis lab using Wireshark. The objective was to capture live network traffic, analyze packet structure, and investigate captured PCAP files from previous Tcpdump exercises.

# Objectives

- Capture live network traffic using Wireshark
- Analyze packet structure and OSI layers
- Inspect HTTP and FTP traffic from PCAP files
- Use “Follow TCP Stream” for session reconstruction
---
Wireshark is a graphical network protocol analyzer used to capture and inspect network packets in real time. It allows deep inspection of packet contents across all OSI layers, making it useful for troubleshooting, security analysis, and forensic investigations.

---

# Wireshark vs Tcpdump

| Wireshark | Tcpdump |
|---|---|
| Graphical interface (GUI) | Command-line tool |
| Deep packet inspection with visuals | Lightweight packet capture |
| Easier analysis of protocols | Faster for live capture |
| Better for investigation and forensics | Better for scripting and quick monitoring |

---

# Part 1 – Live Traffic Capture

Wireshark was launched and the `eth0` interface was selected to begin capturing live network traffic.

A ping request was sent from Kali to the Metasploitable machine to generate ICMP traffic for analysis.
![ping](https://github.com/ilolokerry/Network-Traffic-Analysis-Threat-Investigation-Lab/blob/b8e514bb9dc0515d6719b9ddd5db265ba451bdd9/images/wire/ping.png)
The capture displayed:
- Timestamp of packets
- Source IP and destination IP
- Source and destination ports
- Protocol information

---

 Packet Structure Overview

| Wireshark Section | OSI Layer |
|---|---|
| Frame | Physical / Data Link |
| Ethernet II | Layer 2 – Data Link |
| IP (IPv4/IPv6) | Layer 3 – Network |
| TCP / UDP | Layer 4 – Transport |
| HTTP / FTP / DNS / TFTP | Layer 7 – Application |
| Data | Application Payload |

---

 Packet Inspection Features

The Wireshark interface provides multiple views:
- Bottom-right pane: Hexadecimal representation of packet data
- Bottom-left pane: OSI layer breakdown of each packet

Packets can also be analyzed using:
- “Follow TCP Stream” to reconstruct full conversations between hosts

![layer](https://github.com/ilolokerry/Network-Traffic-Analysis-Threat-Investigation-Lab/blob/b8e514bb9dc0515d6719b9ddd5db265ba451bdd9/images/wire/layer7.png)
- Wireshark live capture interface

---

# Part 2 – PCAP File Analysis

A previously captured PCAP file from the Tcpdump lab was opened in Wireshark for deeper analysis.

```bash
wireshark file.pcap
```
![open](https://github.com/ilolokerry/Network-Traffic-Analysis-Threat-Investigation-Lab/blob/b8e514bb9dc0515d6719b9ddd5db265ba451bdd9/images/wire/open.png)
![ftp](https://github.com/ilolokerry/Network-Traffic-Analysis-Threat-Investigation-Lab/blob/b8e514bb9dc0515d6719b9ddd5db265ba451bdd9/images/wire/ftp.png)

The file contained FTP traffic captured during a login session.

Using “Follow TCP Stream”, the full session was reconstructed, revealing:
- FTP connection establishment
- Username and password exchange
- Successful login response from the server

![stream](https://github.com/ilolokerry/Network-Traffic-Analysis-Threat-Investigation-Lab/blob/b8e514bb9dc0515d6719b9ddd5db265ba451bdd9/images/wire/folow%20ftp.png)
- TCP stream showing FTP login process

---

# Key Skills Demonstrated

- Packet capture and analysis
- Protocol inspection (HTTP, FTP, ICMP)
- Network traffic investigation
- Security monitoring fundamentals

---

# Conclusion

This lab demonstrated how Wireshark can be used to analyze both live and stored network traffic. It provided practical experience in packet inspection, protocol analysis, and understanding network communication at different OSI layers.
