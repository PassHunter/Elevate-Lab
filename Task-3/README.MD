Task 3 – Vulnerability Assessment Using Greenbone/OpenVAS
Date: 17-11-2025
Student: Ayush Madavi
Target Machine: 10.10.10.129
Tool Used: Greenbone Security Assistant (OpenVAS)
🔰 1. Introduction

In this task, I performed a vulnerability assessment on a target machine using Greenbone Security Assistant (OpenVAS).
The objective was to detect misconfigurations, outdated services, and critical vulnerabilities.

🕒 2. Scan Details
Field	Value
Task Name	game
Scan Type	Full and Fast
Scanner	OpenVAS Default
Minimum QoD	70%
Report Count	1
Total Results Found	39 (Filtered to 7 shown)
📊 3. Summary of Detected Vulnerabilities
Severity	Count
🔴 High	1
🟠 Medium	5
🟡 Low	1
🟢 Log	0
⚪ False Positive	0
🖥 4. Host Information
Detail	Value
IP Address	10.10.10.129
Open Ports	10000/tcp, 21/tcp, general/tcp
⚠️ 5. Vulnerabilities Identified
🔴 High Severity (1)
1. Webmin/Usermin Login Cross-Site Scripting (XSS)

Port: 10000/tcp

CVSS Score: 7.5

CVE: CVE-2002-0756

Impact: Allows remote attackers to inject malicious JavaScript.

Fix: Update to Webmin ≥ 0.970.

🟠 Medium Severity (5)
1. FTP Cleartext Login

Port: 21/tcp

Impact: Credentials can be intercepted.

Fix: Enable FTPS / AUTH TLS.

2. Webmin ≤ 1.900 Remote Code Execution (RCE)

Port: 10000/tcp

CVE: CVE-2019-9624

Impact: Unauthenticated attacker can execute arbitrary commands.

Fix: No official vendor patch (software outdated).

3. Webmin 1.880 Information Disclosure

Port: 10000/tcp

CVE: CVE-2018-8712

Impact: Any file can be accessed → /etc/shadow.

Fix: Disable "Can view any file as log file".

4. Missing httpOnly Cookie Attribute

Impact: Cookie accessible to JavaScript.

Fix: Add httpOnly attribute.

5. Cleartext Transmission of Sensitive Information

Impact: Login password sent via HTTP instead of HTTPS.

Fix: Redirect users to HTTPS before login.

🟡 Low Severity (1)
TCP Timestamps Enabled

Impact: Attacker can estimate server uptime.

Fix: Disable timestamps via /etc/sysctl.conf.

📝 6. Conclusion

The target machine contains multiple vulnerabilities including RCE, XSS, cleartext credentials, and information disclosure.
These issues should be patched immediately by updating Webmin and enabling secure communication channels.

This task strengthened my skills in:

Running vulnerability scans

Understanding severity ratings

Reading CVSS scores

Professional reporting and documentation
