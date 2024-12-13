README: Defensive Automation Script
Purpose and Functionality
The Defensive Automation Script automates key actions to enhance system defenses, including:

Blocking malicious domains by modifying /etc/hosts.
Blocking malicious IPs using iptables.
Scanning for malware using known SHA256 hashes.
Generating a detailed log file of all actions for auditing.
This script is ideal for use in Kali Linux or other Linux-based environments.

Instructions for Running the Script
Prerequisites
Operating System: Kali Linux or any compatible Linux distribution.
Root Privileges: Required to make system-level changes.
Dependencies:
iptables (for IP blocking).
sha256sum (for malware hash scanning).
Steps to Run
Save the script as defensive_script.sh.
Open the terminal and navigate to the directory containing the script.
Make the script executable:
bash
Copy code
chmod +x defensive_script.sh
Run the script with root privileges:
bash
Copy code
sudo ./defensive_script.sh
Expected Outputs
A log file named defensive_actions.log will be created in the same directory.
The log will include:
Blocked domains and IPs.
Malware detection results.
A timestamped summary of actions.
Script Details
Configuration
Blocked Domains:
A predefined list of malicious domains (e.g., www.techcadweb.tech, baseinvestments.site) is redirected to 127.0.0.1.
Blocked IPs:
Malicious IPs such as 5.252.178.193 and 84.201.209.98 are blocked using iptables.
Malware Hashes:
Known malware hashes are scanned for across the system.
Functions
Domain Blocking:
Updates /etc/hosts to redirect specified domains to localhost.
IP Blocking:
Adds iptables rules to block incoming and outgoing traffic for malicious IPs.
Malware Scanning:
Scans the filesystem for files matching known SHA256 hashes.
Log Generation:
Records actions in defensive_actions.log.
Sample Output
Log File Example
diff
Copy code
==== Defensive Actions Report ====
Date: [Timestamp]

Blocked Domains:
- www.techcadweb.tech
- baseinvestments.site

Blocked IPs:
- 5.252.178.193
- 84.201.209.98

Malware Scan Results:
- Malware detected with hash 036804e536c9d872f57310662ed730647fae1cb04b96307342b2a73c8789c4f:
  /var/tmp/IMG35.exe
Screenshots to Provide
Terminal screenshot showing script execution.
Contents of the generated defensive_actions.log.
Wireshark traffic filtered for blocked domains or IPs (if applicable).
Troubleshooting
Common Issues
Permission Denied:

Run the script as root:
bash
Copy code
sudo ./defensive_script.sh
Dependencies Not Installed:

Install missing dependencies:
bash
Copy code
sudo apt-get install iptables coreutils
Empty Log File:

Ensure BLOCK_DOMAINS, BLOCK_IPS, and MALWARE_HASHES arrays are populated in the script.
