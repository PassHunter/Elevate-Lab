Task: 3 — Vulnerability Scan Using Greenbone/OpenVAS

(Vulnerability Assessment Report)

Date: 17-11-2025

Student: Ayush Madavi

Tool Used: Greenbone Security Assistant (OpenVAS)

Target Machine: 10.10.10.129 (Game of Thrones VM)

🔰 Introduction

In this task, I performed an automated vulnerability assessment on the target machine using Greenbone/OpenVAS.
The objective was to identify security weaknesses, misconfigurations, and outdated services running on the host.

🕒 Scan Details

Task Name: game

Scan Start: 17-11-2025

Scan Type: Full and Fast

Scanner: OpenVAS Default

Minimum QoD: 70%

Report Count: 1

Total Results: 39 (Filtered: 7)

📊 Summary of Findings
Severity	Count
🔴 High	1
🟠 Medium	5
🟡 Low	1
🟢 Log	0
⚪ False Positive	0

🖥 Host Scanned

IP Address: 10.10.10.129

Ports Detected:

10000/tcp

21/tcp

general/tcp

⚠️ Vulnerabilities Identified
🔴 High Severity (1)
1. Webmin / Usermin Login XSS Vulnerability

Port: 10000/tcp

CVSS Score: 7.5

CVE: CVE-2002-0756

Impact: Allows attackers to inject malicious JavaScript (XSS).

Fix: Update Webmin to v0.970 or later.

🟠 Medium Severity (5)
1. FTP Unencrypted Cleartext Login

Port: 21/tcp

Impact: Credentials can be stolen via sniffing.

Fix: Enable FTPS (AUTH TLS).

2. Webmin ≤ 1.900 Remote Code Execution (RCE)

Port: 10000/tcp

CVE: CVE-2019-9624

Impact: Remote attacker can execute commands.

Fix: No official patch available (service outdated).

3. Webmin 1.880 Information Disclosure

Port: 10000/tcp

CVE: CVE-2018-8712

Impact: Access to arbitrary files → /etc/shadow

Fix: Disable “View any file as log file” setting.

4. Missing httpOnly Cookie Attribute

Impact: Cookies vulnerable to theft via JavaScript.

Fix: Add httpOnly attribute on all session cookies.

5. Cleartext Transmission of Sensitive Info

Impact: Password fields sent over HTTP, not HTTPS.

Fix: Force HTTPS and redirect all users automatically.

🟡 Low Severity (1)
TCP Timestamps Enabled

Impact: Attacker can estimate system uptime.

Fix: Disable by editing /etc/sysctl.conf.

📝 6. Conclusion

The target host contains several medium-to-high impact vulnerabilities, including outdated Webmin versions, unencrypted FTP, and sensitive data exposure.
Critical services should be updated or replaced immediately.

This task helped me understand:
✔ How vulnerability scanners detect issues
✔ How to interpret CVSS scores
✔ How to analyze and document findings professionally
