
# Tcpdump Fundamentals

---

# Project Overview

This hands-on lab focused on learning the fundamentals of Tcpdump through network traffic capture, packet inspection, and protocol analysis within a controlled lab environment.

Using Kali Linux and Metasploitable virtual machines, network communication was monitored and analyzed to understand how packets travel across a network and how traffic can be inspected using packet capture tools.

The lab also explored hexadecimal and ASCII packet analysis, FTP traffic capture, and simulated communication using Netcat.

---

# Lab Environment

```text
                ┌────────────────────┐
                │   Kali Linux VM    │
                │     10.0.0.10      │
                └─────────┬──────────┘
                          │
                    Network Traffic
                          │
                ┌─────────▼──────────┐
                │ Metasploitable VM  │
                │     10.0.0.11      │
                └────────────────────┘
```

---

# Objectives

- Learn fundamental Tcpdump commands
- Capture and analyze live network traffic
- Inspect hexadecimal and ASCII packet data
- Monitor ICMP communication
- Simulate communication using Netcat
- Capture and analyze FTP traffic
- Develop foundational packet analysis skills

---

# Part 1 – Basic Tcpdump Commands

The first step was verifying communication between the two systems.

 Verify Connectivity

The Kali machine successfully communicated with the Metasploitable machine using ICMP ping requests.

```bash
ping 10.0.0.11
```
- Successful ping from Kali to Metasploitable
- ICMP replies visible

---

Access Tcpdump Manual

The Tcpdump manual page was accessed to review command syntax and options.

```bash
man tcpdump
```
---

Display Network Interfaces

The following command was used to display available interfaces on the system.

```bash
tcpdump -D
```
![plain](https://github.com/ilolokerry/Network-Traffic-Analysis-Threat-Investigation-Lab/blob/811fb337c56b363fb94703de5c3836a6534761a0/images/tcpdump/intgerface%20listed.png)
- Tcpdump interface list
  
---

# Part 2 – Sniffing Network Traffic

Network traffic capture was performed on the Ethernet interface.

 Start Packet Capture

```bash
sudo tcpdump -i eth0
```

A second terminal was opened and a ping to Google (8.8.8.8) was performed to generate network traffic.

The capture displayed ICMP request and reply packets between systems.

![ping](https://github.com/ilolokerry/Network-Traffic-Analysis-Threat-Investigation-Lab/blob/811fb337c56b363fb94703de5c3836a6534761a0/images/tcpdump/gogglr%20ping.png)
![details](https://github.com/ilolokerry/Network-Traffic-Analysis-Threat-Investigation-Lab/blob/811fb337c56b363fb94703de5c3836a6534761a0/images/tcpdump/goggle%20detail.png)
- Tcpdump capturing live ICMP traffic with Request and reply packets

---

Analyze Hexadecimal and ASCII Data

The following command was used to inspect packet payloads in hexadecimal and ASCII format to  get more information of the packets.

```bash
sudo tcpdump -i eth0 -X
```

Ping traffic was generated again between Kali and the Metasploitable machine to observe packet contents.
![hex](https://github.com/ilolokerry/Network-Traffic-Analysis-Threat-Investigation-Lab/blob/811fb337c56b363fb94703de5c3836a6534761a0/images/tcpdump/hex%20ping.png)
![details](https://github.com/ilolokerry/Network-Traffic-Analysis-Threat-Investigation-Lab/blob/811fb337c56b363fb94703de5c3836a6534761a0/images/tcpdump/hex%20data.png)

The packet capture displayed the transmitted data (`01234567`) and the identical reply from the target system, confirming successful communication between both hosts.

---

# Part 3 – Simulating Communication with Netcat

A basic communication channel was created using   Tcpdump while Tcpdump monitored the traffic in real time.

Three terminals were used during this exercise.

---

## Start Packet Capture

```bash
sudo tcpdump -i eth0 -X
```

---

## Open Listener on Port 4444

```bash
nc -l -p 4444
```

This command opened port `4444` and started a listener waiting for incoming connections.

---

## Connect to the Listener

```bash
nc 127.0.0.1 4444
```

A connection was established between the two terminals, allowing data to be exchanged.

Basic text and information were transmitted and successfully observed within the packet capture output.

This exercise demonstrated how communication data can be monitored and inspected during network traffic analysis.

📸 Screenshot Placeholder:
- Netcat listener running
- Connection established between terminals
- Tcpdump capturing transmitted text

---

# Part 4 – FTP Packet Capture Analysis

An FTP communication session was captured and analyzed using Tcpdump.

---

## Save Packet Capture to PCAP File

```bash
sudo tcpdump -i eth0 -w file.pcap
```

This command captured live traffic and saved it into a `.pcap` file for later analysis.

📸 Screenshot Placeholder:
- Tcpdump writing packets to file.pcap

---

## Connect to FTP Service

From a second terminal, an FTP connection was initiated to the Metasploitable machine.

```bash
ftp 10.0.0.11
```

A valid username and password were entered successfully to establish the connection.

📸 Screenshot Placeholder:
- FTP login prompt
- Successful FTP authentication

---

## Read Captured PCAP File

After stopping the packet capture, the following command was used to inspect the saved traffic.

```bash
sudo tcpdump -r file.pcap -X
```

The captured FTP session displayed important protocol information such as:
- Login requests
- Authentication responses
- FTP communication details
- Packet payload contents

📸 Screenshot Placeholder:
- Reading the PCAP file
- FTP traffic visible in capture
- Login request and success messages

---

# Skills Demonstrated

- Packet capture and filtering
- ICMP traffic analysis
- Hexadecimal and ASCII packet inspection
- Protocol analysis
- FTP traffic investigation
- PCAP analysis
- Network traffic monitoring
- Basic network forensics
- Packet-level communication analysis

---

# Key Learning Outcomes

This lab provided practical experience using Tcpdump for:
- capturing and inspecting live traffic
- understanding packet structures
- analyzing network communication behavior
- monitoring transmitted data
- investigating protocol traffic

The project helped strengthen foundational skills in packet analysis and network traffic investigation workflows.
