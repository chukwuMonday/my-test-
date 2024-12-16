README: Defensive Automation Script - Purpose, Functionality, and Instructions
Purpose and Functionality
The Defensive Automation Script is designed to automate critical actions for enhancing system security by performing the following tasks:

Blocking Malicious Domains: Modifies /etc/hosts to redirect traffic from specified malicious domains to 127.0.0.1.
Blocking Malicious IPs: Utilizes iptables to block traffic from malicious IP addresses.
Scanning for Malware: Scans the system for known malware using SHA256 hashes.
Generating Logs: Creates a detailed log file for auditing purposes, documenting all actions taken.
This script is best suited for use in Kali Linux or any compatible Linux-based operating systems.

Instructions for Running the Script
Prerequisites
Operating System: Kali Linux or any Linux distribution with compatibility.
Root Privileges: Required to execute system-level changes.
Dependencies:
iptables (for IP blocking)
sha256sum (for scanning known malware hashes)
Steps to Run the Script
Save the script as defensive_script.sh.
Open a terminal and navigate to the directory containing the script.
Make the script executable:
bash
Copy code
chmod +x defensive_script.sh
Run the script with root privileges:
bash
Copy code
sudo ./defensive_script.sh
Expected Outputs
A log file named defensive_actions.log will be created in the same directory. This log will include:
A list of blocked domains and IPs
Malware detection results
A timestamped summary of all actions performed
Script Details
Configuration
Blocked Domains: A predefined list of malicious domains (e.g., www.techcadweb.tech, baseinvestments.site) will be redirected to 127.0.0.1.
Blocked IPs: Malicious IPs such as 5.252.178.193 and 84.201.209.98 will be blocked via iptables.
Malware Hashes: Known malware hashes are checked against files on the system.
Functions
Domain Blocking: The script updates /etc/hosts to redirect specified malicious domains to localhost.
IP Blocking: Adds iptables rules to block traffic from identified malicious IP addresses.
Malware Scanning: The script scans the filesystem for files that match known malware SHA256 hashes.
Log Generation: All actions (blocked domains, IPs, malware scans) are recorded in defensive_actions.log.
Sample Output Log File
bash
Copy code
==== Defensive Actions Report ====
Date: 12/12/2024

Blocked Domains:
- www.techcadweb.tech
- baseinvestments.site

Blocked IPs:
- 5.252.178.193
- 84.201.209.98

Malware Scan Results:
- Malware detected with hash `036804e536c9d872f57310662ed730647fae1cb04b96307342b2a73c8789c4f`: /var/tmp/IMG35.exe
Screenshots to Provide
Terminal screenshot showing the script execution.
Contents of the generated defensive_actions.log file.
Wireshark traffic filtered for blocked domains or IPs (if applicable).
Troubleshooting
Common Issues
Permission Denied:

Ensure you are running the script with root privileges:
bash
Copy code
sudo ./defensive_script.sh
Missing Dependencies:

Install any missing dependencies:
bash
Copy code
sudo apt-get install iptables coreutils
Empty Log File:

Ensure the arrays BLOCK_DOMAINS, BLOCK_IPS, and MALWARE_HASHES in the script are populated with appropriate values.
By following these instructions, users can effectively run the Defensive Automation Script to protect their systems from potential cyber threats.



