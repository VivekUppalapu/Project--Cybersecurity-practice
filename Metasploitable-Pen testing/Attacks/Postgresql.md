# Postgresql
I focused on attacking Postgresql that is present in the Metasploitable 2 machince. 
For the entirety of this attack, I chose to do it all in Metasploit instead of switching from the terminal to Metasploit. 
## Login Utility
My first step was to see if I can get any credentails of the Postgresql in Metasploitable 2. 
I used the Login Utility present in Metasploit, present in the auxilary module, auxiliary/scanner/postgres/postgres_login.
When run, it tries the default usernames and passwords list that Metasploit has for postgress and tries it on the template1 database,
a common database present in most postgresql installations. 
In this case, it was sucessful, providing the credentails of postgres and postgres. With these credentails, multiple things can be done:
1. Can login to postgresql and discover other databases
2. Look into tables and data within them
3. Execute SQL commands, getting more information out what kind of data is present
4. Be able to view and extract sensitive data present in these tables within certain databases

## Read File
From checking login credentials, I then moved to another postgresql module, auxiliary/admin/postgres/postgres_readfile. 
This module, found in Metasploit, allows the reading of files from a system running a PostgreSQL database. This module exploits PostgreSQL's COPY command, which can read server-side files if the database is misconfigured or improperly secured. 
Thus, once the filepath is provided, in this case /etc/passwd, the module uses PostgresSQL commands to read it, which it does and 
displays it. I did try with /etc/shadow, but it did not allow me due to priviledges since I was not the highest user logging on. 
Still, the /etc/passwd file still provides a lot of information that can be used for future attacks. This includes:
1. Services on the platform
2. Usernames for possible brute-force/social engineering
3. Privildge escalation identification and attempts

# Remote Access
Looking through the postgessql modules present in Metasploit, I found linux/postgres/postgres_payload. This exploit connects to a vulnerable postgresql database with valid credentials, uses its ability to execute system commands to deliver a payload, which is a reverse shell, providing remote access, using Meterpreter. 
## Exploration with Meterpreter
Once in the system and using Meterpreter, I explored the target system, going through the various directories, including logs, user, and root. Within root, I looked into the various files and directories present, including the ssh directory. Within it, I looked at the authorized keys as there are neumerous things that can be done with them including:
  1. Stealing private key to authenticate sessions with public key already is authorized
  2. Adding attacker's own public key to the authorized keys file, ensuring access
I then used the search functions to search for files within, using  -f(find pattern) and * for wildcard, using it to find all documents(.doc), log files(.log) to see if I can find anything of importance. I looked into files that I felt were important, but didn't get anything important from them.
## Post modules
Post modules in Metasploit are tools that are used after sucessful exploitation, and in this case, after exploitation of postgresql, I can use post modules for various purposes, including:
  1. Information gathering
  2. Priviledge escalation
  3. Lateral Movement
In my case. I used post modules for information gathering, specifically, configuration files, network and user history.
### post/linux/gather/enum_configs
This post module searches for commonly installed applications and services, and collects the configuration files. These files contain system and application settings, which can be used to identify potential weakness/vulnerbilities. 
### post/linux/gather/enum_network
This post module gathers network information about the system, including IPTable rules, Network interfaces, wireless connections, Open and listenting ports, Network connections that are active, DNS information and SSH configuration. This networking information can be used to understand the network infastructure, see where to laterally move to(based on open and listening ports), understand and evaluate the network security present by looking at the IPTable rules, and looking to misconfigurations or weak settings in SSH configuration. 
### post/linux/gather/enum_users_history
This post module gathers user informaiton, including Shell History, database applications command history, Vim editor history, when they last logged in, and sudoers file contents. This information can be used to understand user priviledges and sudo access rights, and Login patterns to posibly understand user behavior, previous commands executed(possibly exposing sensitive/important information).
