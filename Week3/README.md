Week 3 – Web Application Vulnerability Assessment
Objective

The objective of this lab was to perform basic web application security testing on a vulnerable web application. The testing included identifying vulnerabilities, exploiting them, and analyzing the possible impact of those vulnerabilities.

The testing was conducted in a controlled lab environment using a vulnerable application for educational purposes.

Target Information

Application: Damn Vulnerable Web Application
Target IP Address: 192.168.56.102
Application URL: http://192.168.56.102/dvwa

Attacker Machine: Kali Linux

Tools Used

Kali Linux

Nmap

sqlmap

Web Browser

Testing Workflow

The following penetration testing workflow was followed during the lab:

Target Identification

Network Scanning

Vulnerability Discovery

Exploitation

Post-Exploitation

Documentation and Reporting

Step 1 – Network Scanning

The target machine was scanned to identify open ports and services.

Command used:

nmap -sV 192.168.56.102

Result:
Port 80 (HTTP) was found open, indicating the web application service running on the target.

Screenshot reference:
screenshots/02_nmap_scan.png

Step 2 – SQL Injection Testing

The SQL Injection vulnerability was tested in the DVWA SQL Injection module.

Example payload used:

1' OR '1'='1

Result:
The application returned multiple records, confirming that the input was being executed inside the SQL query.

Screenshot reference:

screenshots/03_sql_injection.png
Step 3 – Automated SQL Injection using sqlmap

The vulnerability was further tested using sqlmap to automate the exploitation process.

Command used:

sqlmap -u "http://192.168.56.102/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --dbs

Result:
The tool successfully identified multiple databases including the dvwa database.

Screenshot reference:

screenshots/04_sqlmap_dbs.png
Step 4 – Database Data Extraction

The users table from the dvwa database was extracted.

Command used:

sqlmap -u "http://192.168.56.102/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" -D dvwa -T users --dump

Result:
Usernames and password hashes were successfully retrieved.

Screenshot reference:

screenshots/06_sqlmap_dump.png
Step 5 – Reflected XSS Testing

Reflected Cross-Site Scripting was tested using the DVWA XSS module.

Payload used:

<script>alert('XSS')</script>

Result:
A JavaScript alert was displayed in the browser, confirming the vulnerability.

Screenshot reference:

screenshots/05_reflected_xss.png
Post-Exploitation Analysis

After successful exploitation, it was demonstrated that an attacker could extract sensitive data from the database and execute JavaScript in the victim’s browser.

Possible impacts include:

Extraction of user credentials

Session hijacking through cookie theft

Execution of malicious scripts in user browsers

Folder Structure
Week3
│
├── Web_Application_Testing_Report.pdf
├── README.md
├── notes.md
│
└── screenshots
    ├── 01_dvwa_login.png
    ├── 02_nmap_scan.png
    ├── 03_sql_injection.png
    ├── 04_sqlmap_dbs.png
    ├── 05_reflected_xss.png
    ├── 06_sqlmap_dump.png
Documentation

The detailed lab report containing explanation of all steps, screenshots, and analysis is available in:

Web_Application_Testing_Report.pdf
Conclusion

This lab demonstrated how common web application vulnerabilities such as SQL Injection and Cross-Site Scripting can be identified and exploited. The testing highlights the importance of proper input validation, secure coding practices, and regular security assessments to protect web applications from potential attacks.



If you want, I can also give you a perfect screenshot order + exact filenames teachers expect (most students lose marks here) so your Week3 GitHub submission looks very professional.
