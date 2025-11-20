Task 5: Packet Capture \& Protocol Analysis Using Wireshark

Student: Ayush Madavi

Date: 20-11-2025

Attacker Machine: Windows 11 / Kali Linux (any system running Wireshark)

Target: Live Network Traffic (Web Browsing \& DNS Requests)

🔰 Introduction

For this task, I used Wireshark to capture live network traffic from my active network interface. The goal was to observe real-time packets flowing through my system, identify multiple network protocols, and understand how different layers of communication operate on a typical network.

I performed a 1-minute packet capture, generated traffic by browsing websites, filtered packets by protocol, and analyzed the captured data. The output was saved as a .pcap file for submission and review.

🎯 Objective

Capture live network packets and identify at least three protocols (e.g., TCP, DNS, HTTP), providing a short analysis of each.

🛠 Tools Used

Wireshark (latest version) – Packet capturing \& analysis

Windows / Kali Linux – Operating environment

Web Browser – To generate traffic

Network Interface (Wi-Fi/Ethernet) – Source of packet flow

📡 Step 1: Start Wireshark Capture

I launched Wireshark and selected my active Wi-Fi interface.

Live packets immediately began appearing in the capture window.

🌐 Step 2: Generate Network Traffic

To ensure a variety of packets were captured, I:

Opened multiple websites

Triggered DNS lookups

Browsed pages to generate TCP and HTTP/HTTPS requests

This helped populate the capture with different protocol types.

🛑 Step 3: Stop the Capture

After approximately 1 minute, I stopped the capture to prevent unnecessary clutter and saved it.

🔎 Step 4: Protocol Filtering

I used Wireshark filters to isolate key protocols:

Protocol	Filter Used	Purpose

TCP	tcp	Transport layer communication

UDP	udp	Connectionless transmission

DNS	dns	Domain name lookups

HTTP	http	Web communication (if unencrypted)

🧪 Protocol Summary (Identified in live-network.pcap)

At least the following protocols were identified during analysis:

🔹 TCP

Used for reliable data delivery

Present in most website loads

Common in HTTPS/TLS connections

🔹 UDP

Used in lightweight communication

Supports DNS lookups

🔹 DNS

Essential for resolving domain names

Queries \& responses clearly visible

🔹 (Optional) HTTP / TLS

Seen if visiting non-HTTPS sites

TLS handshakes appear for HTTPS

📘 Explanation of Common Protocols

🔹 TCP (Transmission Control Protocol)

Function: Reliable, connection-oriented communication

Security Concerns:

Can reveal hosts, ports, and active services

Importance: Foundation of most internet communication

🔹 UDP (User Datagram Protocol)

Function: Fast, stateless communication

Security Concerns:

No reliability; susceptible to spoofing

Importance: Backbone of DNS, streaming, and VoIP

🔹 DNS (Domain Name System)

Function: Resolves domain names to IP addresses

Security Concerns:

DNS poisoning

Zone transfer attacks

Importance: Critical part of any network communication

✔️ Conclusion

This task successfully demonstrates how to perform live packet capture using Wireshark, filter traffic by protocol, and analyze the structure and purpose of network communication.

By identifying key protocols such as TCP, UDP, and DNS, I gained practical understanding of packet flow and protocol behavior in real-world environments.


