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
displays it. 
