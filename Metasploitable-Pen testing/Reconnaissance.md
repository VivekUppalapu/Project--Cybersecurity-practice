# Nmap
## nmap -sS -sV 192.168.191.128
From my Kali VM, I used nmap to scan for open ports and services within the Metasploitable 2 VM box. The command I used is shown in the header, with -sS and -sV used, stealth scan and service/version informatoin. The sealth scan(sS) is a TCP SYN scan where a SYN packet and analyzes the result to determine whether a port is open or not, doing a half-open scan. This makes the SYN scan harder to detect. sV looks into the version or service used by each port, providing more information to better understand what I am dealing with to formulate a plan of attack

## nmap --script vuln 192.168.191.128
I then, after seeing the ports and services/version within them, ran this command, which runs all the scripts under the vuln category of NSE(Nmap Scripting Engine), which check for known vulnerabilities. This helped me identify which ports had vulnerbilities, as some were explicit in the vulnerbilities present, and which ports had areas to look into. 

