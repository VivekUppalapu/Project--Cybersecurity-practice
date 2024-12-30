# Usermap script
The smb(Server Messenger Block) present in Metasploitable 2 is Samba smbd 3.0.20 Debian. 
Based on this version and name, I used searchsploit, a command-line tool that allows you to search and use exploit data, which comes from the Exploit-DB database. 
The search results provided me with multiple attacks, including usermap script, found in Metasploit. I opened up Metasploit and found usermap script to understand it better.
This Smaba exploit, when used, allows attackers to include special shell characters in usernames, which Samba improperly processes, enabling remote command execution. 
Thus, this script has usernames with shell characters included, so that Samba will process it improperly to enable remote command execution. Write more
