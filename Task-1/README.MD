#Task 1: Scan Your Local Network for Open Ports

## Student: Ayush Madavi

## Date:  13-111-2025

## Attacker Machine: Kali Linux

## Target Machine: Game of Thrones VM (10.10.10.129)

---

## 🔰 Introduction

For this task, I created a safe and isolated virtual lab environment consisting of two virtual machines: **Kali Linux** (used for scanning and analysis) and the **Game of Thrones VM** (used as the target system). I first used **Netdiscover** to identify active devices within the network and locate the target machine’s IP address. Once the target was identified, I performed multiple **Nmap scans** to enumerate open ports, identify running services, and analyze the potential vulnerabilities of the system.

---

## 🎯 Objective

Scan the local network to discover open ports and understand the security exposure of devices.

---

## 🛠 Tools Used

* **Kali Linux** (Attacker VM)
* **Game of Thrones VM** (Target)
* **Netdiscover** – for network discovery
* **Nmap 7.95** – for port scanning and enumeration
* **VirtualBox/VMware** – private isolated network

---

## 📡 Step 1: Host Discovery

To discover active hosts in my isolated network, I used:

```
netdiscover -r 10.10.10.0/24
```

This revealed the target IP address: **10.10.10.129**.

---

## 🔎 Step 2: Nmap Scanning

### Basic SYN Scan

```
sudo nmap -sS 10.10.10.129 -oN scan-results.txt
```

### Aggressive Enumeration Scan

```
sudo nmap -A 10.10.10.129 -oN got-full.txt
```

### Vulnerability Script Scan

```
sudo nmap --script vuln 10.10.10.129 -oN got-vuln.txt
```

---

## 🧪 Scan Results Summary (Initial SYN Scan)

| Port      | State    | Service    | Risk   |
| --------- | -------- | ---------- | ------ |
| 21/tcp    | open     | FTP        | Medium |
| 22/tcp    | open     | SSH        | Low    |
| 53/tcp    | open     | DNS        | Medium |
| 80/tcp    | open     | HTTP       | Medium |
| 143/tcp   | filtered | IMAP       | Low    |
| 3306/tcp  | filtered | MySQL      | Low    |
| 5432/tcp  | open     | PostgreSQL | High   |
| 10000/tcp | open     | Webmin     | High   |

---

📘 Research on Common Services

A detailed analysis of each identified service was conducted to understand its purpose, how it typically behaves in a network, and what security implications it may introduce. This research step forms the foundation for identifying potential vulnerabilities and evaluating the overall security posture of the target system.

🔹 FTP (Port 21)

Function: File Transfer Protocol is used for transferring files between a client and server. Common Use Cases: Uploading/downloading files, legacy system management. Normal Behavior: Operates in plaintext; supports anonymous or authenticated access. Security Concerns:

Credentials and data are sent unencrypted.

Anonymous login may expose sensitive files.

Older FTP servers contain known exploits. Why It Matters in Pentesting: Often an initial foothold point, especially in vulnerable VMs.

🔹 SSH (Port 22)

Function: Secure Shell provides encrypted remote management. Common Use Cases: Remote administration, file transfers (SCP), tunneling. Normal Behavior: Encrypted communication using keys or passwords. Security Concerns:

Weak passwords lead to brute-force attacks.

Outdated SSH versions may allow privilege escalation. Why It Matters: A secure service but often the gateway to post-exploitation if misconfigured.

🔹 DNS (Port 53)

Function: Resolves domain names to IP addresses. Common Use Cases: Network communication, internal name resolution. Normal Behavior: Accepts and responds to DNS queries. Security Concerns:

Misconfigured DNS can allow zone transfers.

Open DNS resolvers may be used in DDoS amplification attacks.

Information leakage from DNS queries. Why It Matters: Attackers often enumerate DNS to find hidden subdomains.

🔹 HTTP (Port 80)

Function: Web service for hosting websites or applications. Common Use Cases: Hosting dashboards, content, admin panels. Normal Behavior: Serves static or dynamic web content over plaintext. Security Concerns:

Outdated web servers have known vulnerabilities.

Directory listing may leak sensitive files.

Exposed admin panels lead to full compromise. Why It Matters: Web services are the most commonly attacked entry point.

🔹 PostgreSQL (Port 5432)

Function: Advanced open-source relational database system. Common Use Cases: Application backends, data storage. Normal Behavior: Accepts SQL queries from authenticated users. Security Concerns:

Default credentials frequently left unchanged.

Remote access drastically increases the attack surface.

Unpatched versions have authentication bypass vulnerabilities. Why It Matters: Database compromise often means total data exposure.

🔹 Webmin (Port 10000)

Function: Web-based system administration tool. Common Use Cases: Managing users, services, packages, and system configuration. Normal Behavior: Web interface accessible via HTTP/HTTPS. Security Concerns:

Historically vulnerable to remote code execution (RCE).

Should never be exposed without TLS.

Gives full root-level control if compromised. Why It Matters: One of the highest-risk services when exposed to a network.

---

## 📝 Detailed Risk Analysis

### 1. FTP – Medium Risk

FTP is unencrypted and vulnerable to sniffing attacks. Exposure may lead to credential leaks.

### 2. SSH – Low Risk

Secure but can be brute-forced if weak passwords are used.

### 3. DNS – Medium Risk

Unexpected service that could be abused if misconfigured.

### 4. HTTP – Medium Risk

May reveal outdated or vulnerable components.

### 5. PostgreSQL – High Risk

Open database services are a major attack vector. Misconfigurations can expose sensitive data.

### 6. Webmin – High Risk

Webmin has multiple known vulnerabilities including remote code execution.

---

## 📁 Files Included in This Task

* **scan-results.txt** – Initial SYN scan
* **got-full.txt** – Aggressive enumeration
* **got-vuln.txt** – Vulnerability script scan
* **screenshots/** – Terminal output, discovery, and scan proofs
* **README.md** – Documentation

---

## ✔️ Conclusion

This task successfully demonstrates basic network reconnaissance, host identification, port scanning, and service enumeration using Kali Linux and Nmap. The Game of Thrones VM revealed several open services, including high-risk ones such as PostgreSQL and Webmin. The findings highlight the importance of securing exposed services, configuring firewalls properly, and keeping software updated.
