# Task 4: Firewall Setup and Testing (Windows/Linux)
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Overview

The goal of this task was to configure a firewall, apply basic rules to control network traffic, and test whether those rules work as expected. I worked with UFW on Linux and Windows Firewall on a Windows VM.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Tools Used

- Linux (Ubuntu 22.04) — UFW (Uncomplicated Firewall)
- Windows 10 — Windows Defender Firewall with Advanced Security
- Telnet client and nmap for testing

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# UFW - Linux Steps

1. Check current firewall status
bash
                     sudo ufw status verbose


2. Block incoming traffic on port 23 (Telnet)

bash
                     sudo ufw deny 23


3. Test if port 23 is blocked

* Used telnet localhost 23 (connection refused)
* Also checked with nmap:

bash
                     nmap -p 23 localhost

4. Allow SSH (port 22)

bash
                    sudo ufw allow 22


5. Remove Telnet rule after test

bash
                   sudo ufw delete deny 23


6. Final status check

bash
                   sudo ufw status


# Windows Firewall Steps

1. Launch Firewall GUI

* Press `Win + R`, type `wf.msc`, Enter

2. Create a new inbound rule to block port 23

* New Rule > Port > TCP > Specific local ports: `23`
* Action: **Block the connection**
* Apply to all profiles
* Gave it the name "Block Telnet Test"

3. Test rule

* Tried connecting via Telnet from another system — failed as expected

4. Add rule to allow SSH (port 22)

* Same steps, but **Allow** instead of Block

5. Delete Telnet rule

* Right-click > Delete the rule after testing

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


