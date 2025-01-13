# Network Set-up
To ensure that I did not have any potential legal or network issues, I chose to setup the two virual boxes of Kali and Metasploitable to Host-only instead of NAT. 
## Why Host-Only
By using host-only, I would ensure that the VMs are isolated from the internet and my local network, with the only communication being between Kali and Metasploitable.
## IP addresses and DHCP
Within the Virtual Network Editor, I created a new VMNet that is set to Host-Only with DHCP on, so that both Kali and Metasploitable 2 devices are provided IP addresses within the 192.168.128.0/24 range.
