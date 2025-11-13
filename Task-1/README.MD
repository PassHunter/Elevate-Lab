# Elevate Lab – Task 1: Local Network Port Scanning & Risk Analysis

## Student: Ayush Madavi

## Date: 2025-11-13

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

## 📘 Research on Common Services

### FTP (21)

* Transfers data in plaintext
* May allow anonymous login
* **Risk:** Medium

### SSH (22)

* Secure remote login service
* Target for brute-force attacks
* **Risk:** Low

### DNS (53)

* Domain name resolution
* Misconfiguration may allow DNS recursion
* **Risk:** Medium

### HTTP (80)

* Web server service
* Possible outdated web pages or exploits
* **Risk:** Medium

### PostgreSQL (5432)

* Open database service
* Default credentials common in vulnerable VMs
* **Risk:** High

### Webmin (10000)

* Web-based system administration tool
* Historically contains RCE vulnerabilities
* **Risk:** High

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
