# Nmap
## Uses of Nmap for Metasploitable 2
From my Kali VM, I used nmap to scan for open ports and services within the Metasploitable 2 VM box. I used the -sS option of stealth scanning as well as the -sV, for service 
versions. The scan provided me all the open ports and services used within each of these services. The services I focused on for attacks included FTP service(VSFTPD) on port 21,
Samba SMB on port 139/445, Apache Tomcat on port 8180, Apache on port 80, MySQL on port 3306 and Postgresql on port 5432. 

# Nikto 
I used Nikto for Apache on port 80, to see what vulnerbilities are present that can be exploited, as it is a web scanner which looks for vulnerbilities of the host provided. 
In this case, the host is the IP address of Metasploitable 2. 
