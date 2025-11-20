Task 4: Firewall Configuration \& Traffic Filtering

Student: Ayush Madavi

Date: 18-11-2025

Attacker Machine: Parrot OS

Target Machine: Kali Linux (10.10.10.128)

🔰 Introduction



In this task, I configured and tested firewall rules using UFW (Uncomplicated Firewall) on Kali Linux.

The objective was to:



View existing firewall rules



Add a rule to block a specific port



Test the rule from another machine



Allow SSH and verify connection



Restore the firewall to its original state



This demonstrates how a firewall filters network traffic and helps secure a system.



🛠 Steps Performed

1\. Checked Firewall Status



Command used:



sudo ufw status





🔹 The firewall was active

🔹 Ports 22, 23, 9392 were allowed



2\. Added Rule to Block a Port (SSH port 22)



Command used:



sudo ufw deny 22/tcp





Result:

22/tcp DENY and 22/tcp (v6) DENY were created.



This means SSH traffic is now blocked.



3\. Verified Updated Firewall Rules



Command:



sudo ufw status





The rule showed as DENY successfully.



4\. Tested the Block From Parrot OS



From Parrot:



ssh kali@10.10.10.128





⚠ Output:



ssh: connect to host 10.10.10.128 port 22: Connection refused





This confirms the firewall successfully blocked SSH traffic.



5\. Verified SSH Access Before Blocking



Before denying port 22, SSH worked normally:



ssh kali@10.10.10.128





I logged in successfully and ran:



whoami





Output: kali



This proves that the block rule actually changed the behavior.



6\. Discovered Network Hosts



Using:



netdiscover





Found:



10.10.10.1



10.10.10.128



10.10.10.254



This confirmed both attacker and target machines were reachable.



7\. Restored Firewall State (Remove Deny Rule)



Command:



sudo ufw delete deny 22/tcp





This re-enabled SSH access.



📌 Commands Used

sudo ufw status

sudo ufw deny 22/tcp

sudo ufw status numbered

sudo ufw delete deny 22/tcp

ssh kali@10.10.10.128

netdiscover

whoami



🔒 Summary: How Firewall Filters Traffic



The firewall checks every incoming packet and compares it with the rule list.

If a rule matches (ALLOW or DENY), the packet is accepted or dropped.



UFW is a frontend for iptables and simplifies rule management.

Rules can be based on:



Port number



Protocol



IP address



Direction (IN/OUT)



In this task, the firewall successfully blocked SSH and controlled access to the system.



📝 Conclusion



All steps for Task 4 were successfully completed:



✔ Listed firewall rules

✔ Added deny rule

✔ Tested block from another machine

✔ Allowed SSH

✔ Restored firewall settings

✔ Documented commands

✔ Explained firewall behavior

