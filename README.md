# PRODIGY_CS_05
A packet sniffer tool that captures and analyzes network packets

# Packet Analyzer (Educational)

> **IMPORTANT:** This project is designed **strictly for educational and research** purposes. It demonstrates how to capture and analyze network packets using Python and the Scapy library. **Do not** use this script to monitor or intercept data on networks you do not own or have explicit permission to analyze. Unauthorized network sniffing can be illegal and unethical.


# Table of contents

* [Overview]
* [Features]
* [Requirements]
* [Installation]
* [Usage]
* [How it works]
* [Configuration]
* [Safety, Ethics & Legal]
* [Troubleshooting]


# Overview

This **Packet Analyzer** is a simple Python-based network packet sniffer built with the Scapy library. It captures live packets on your system, extracts IP, TCP, and UDP layer information, and prints human-readable summaries to the console. This tool is excellent for learning about network protocols and packet structures.


# Features

* Captures live network traffic using Scapy.
* Displays source and destination IP addresses, and protocol numbers.
* Extracts and attempts to decode TCP and UDP payloads.
* Safe handling of decoding errors to prevent crashes.
* Simple and customizable architecture.



# Requirements

* Python 3.8 or higher
* Scapy library

Install the dependency with:

```bash
pip install scapy
```



# Installation

1. Copy the script into a file, e.g. `packet_analyzer.py`.
2. Ensure Scapy is installed (see Requirements).
3. Run the script in an environment where you have permission to monitor traffic (e.g., your own local network).

> **Note:** On some systems, you may need to run with elevated privileges (Administrator or `sudo`) to capture packets.



# Usage

Run the script from the terminal:

```bash
python packet_analyzer.py
```

Output example:

```
Source IP: 192.168.1.10 | Destination IP: 172.217.174.46 | Protocol: 6
TCP Payload
Source IP: 192.168.1.10 | Destination IP: 8.8.8.8 | Protocol: 17
UDP Payload
```

Stop the program with **Ctrl + C**.



# How it works

1. The script defines a **callback function** (`packet_callback`) that runs each time a packet is captured.
2. It checks whether the packet contains an IP layer and extracts key details:

   * Source IP (`src_ip`)
   * Destination IP (`dst_ip`)
   * Protocol number (`proto`)
3. If the packet contains a TCP or UDP layer, the script attempts to extract and decode its payload.
4. All information is printed to the console for live monitoring.
5. The `start_sniffing()` function initiates Scapy’s `sniff()` method, continuously capturing and analyzing packets.



# Configuration

You can modify the behavior of the analyzer easily:

* **Filter packets:** Add filters to `scapy.sniff()` (e.g., `filter="tcp"` to only capture TCP traffic).
* **Save results:** Redirect printed output to a file for later analysis.
* **Batch analysis:** Modify the callback to count and log specific protocols.
* **Decode more layers:** Extend the code to inspect HTTP, DNS, or ICMP layers.


# Safety, Ethics & Legal

* Only capture traffic on networks you own or are authorized to test.
* Do not use this tool to monitor private or third-party communications.
* Unauthorized interception of data is illegal under many privacy and cybercrime laws.
* For learning, use **virtual machines** or **isolated lab networks**.



# Troubleshooting

* **Permission denied:** Try running as administrator or with `sudo`.
* **No packets captured:** Ensure your network interface supports promiscuous mode and Scapy has permission to access it.
* **Unicode decode errors:** Already handled in the code by ignoring undecodable bytes.
* **Import errors:** Install Scapy using `pip install scapy`.

