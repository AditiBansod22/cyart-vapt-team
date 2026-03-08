# Nmap Scan

This folder contains the results of the network scanning performed on the Metasploitable2 virtual machine using the Nmap tool.

Nmap was used to identify open ports and the services running on the target system. The scan helped in understanding the network exposure of the machine and identifying possible entry points for attackers.

Command used for scanning:

nmap -sV <target_ip>

The scan revealed several open ports such as FTP, SSH, HTTP, and SMB services. These services may contain vulnerabilities if they are outdated or improperly configured.

The screenshot included in this folder shows the output of the Nmap scan performed during the vulnerability assessment process.
