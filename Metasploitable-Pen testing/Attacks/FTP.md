# FTP Attack
## Malicious Backdoor exploitation
The FTP version present in Metasploitable 2 was vsFTPd 2.3.4. Based on the nmap vulners script, this version has a backdoor that can be exploited. 
## Metasploit
Using Metasploit, I searched for vsftp exploits present and found the exploit. The exploit, exploit/unix/ftp/vsftpd_234_backdoor, exploits a malicious backdoor added into the download archive of VSFTPD. 
### exploit/unix/ftp/vsftpd_234_backdoor
This exploit has options, requiring the target host(IP address) and the port. After running it, a backdoor will open, connecting me to the target. 
### Post exploitation
I now have access to the target computer and can traverse through it. 
My first step was to check my access, and using whoami, I saw that I was the root user. This meant that I could access the sensitive files that only had root permissions to view. The file that I accessed was the /etc/shadow file, as it had all the hashed passwords within the system. 


