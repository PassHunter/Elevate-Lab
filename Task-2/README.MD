Task 2: Phishing Email Analysis

Student: Ayush Madavi

Date: 14-11-2025

Environment: Controlled Cybersecurity Lab (Phishing Simulation)

🔰 Introduction

For this task, I analyzed a simulated phishing email designed to look like a Microsoft security alert. The purpose of the exercise was to examine the email content, sender details, embedded link, and social engineering techniques used by attackers. By carefully evaluating the message headers, grammar, domain information, urgency tactics, and hyperlink behavior, I identified multiple indicators proving that the email is a 100% phishing attempt. This analysis helps improve my detection skills and strengthens real-world email security awareness.

🎯Objective

Analyze a suspicious email and identify phishing indicators to understand how attackers trick users into revealing sensitive information.

🛠 Tools Used

Gmail/Outlook Draft View – to display the phishing email

Mouse Hover Link Preview – to observe real URL behind the link

WHOIS Lookup / Domain Check – to analyze fake domain

Security Awareness Techniques – to identify social engineering red flags

Markdown (README.md) – to document findings

📩 Email Examination

Below is the exact simulated phishing email used for analysis:

From: Microsoft Account Support <security-update@micosoft-verification.com>

To: you@example.com

Subject: ⚠ Immediate Action Required: Your Microsoft Account Has Been Temporarily Locked

Dear User,

We detected unusual sign-in activity on your Microsoft account from a new device.
To protect your account, we have temporarily locked access until we can verify that this was you.

If this activity was not performed by you, you must verify your identity within the next 24 hours,
otherwise your account may be permanently suspended.

Please use the secure portal below to restore access:

👉 Verify Your Account Now
https://microsoft-login-security-check.com/verify/user
(This is a fake, non-functional URL created only for training—DO NOT USE.)

For your safety, failure to confirm your details may result in losing access to emails,
OneDrive files, and linked devices.

If you believe this message was sent to you in error, please ignore it.

Thank you,  
Microsoft Account Security Team

🔎 Identifying Phishing Indicators

1️⃣ Fake Sender Address

The email claims to be from Microsoft, but the sender address is:
security-update@micosoft-verification.com

Red flags:

“micosoft” is misspelled (missing r → Microsoft)
Domain micosoft-verification.com is NOT an official Microsoft domain
Microsoft uses domains like:
microsoft.com
account.microsoft.com
login.microsoftonline.com
This clearly shows email spoofing.

2️⃣ Urgent or Scary Language

The subject contains:
"⚠ Immediate Action Required"

Inside the email:
“verify within the next 24 hours”
“your account may be permanently suspended”
Attackers use urgency to force quick action without thinking.

3️⃣ Suspicious Link (Hover Test)

Displayed link:
https://microsoft-login-security-check.com/verify/user

Issues:
Not a real Microsoft domain
Extra words (“login-security-check”) commonly used in phishing
Missing official Microsoft formatting
The URL is designed to look legitimate but is completely fake
When you hover the mouse, the real destination link is not Microsoft, confirming a phishing site.

4️⃣ Generic Greeting

The email begins with:
Dear User,
Legitimate Microsoft emails ALWAYS address you by your full name.
Generic greetings are typical in mass phishing campaigns.

5️⃣ Grammar & Spelling Errors

micosoft → should be microsoft
Awkward sentence structures
Slight grammar inconsistencies
Professional companies rarely make these mistakes.

6️⃣ Fake Security Warning

The email claims:
“Your Microsoft account has been temporarily locked.”
Real Microsoft alerts appear in the Security Dashboard, not through random emails with clickable links.

✔️ Conclusion

This task successfully demonstrates how to identify phishing attempts by analyzing the sender domain, embedded URLs, urgency tactics, and grammar issues. The email used multiple social engineering techniques to trick the recipient into clicking a fake verification link. Through this analysis, I gained hands-on experience in phishing detection, email header inspection, and reporting — essential skills in cybersecurity.
