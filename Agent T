A step by step walk through for the Agent T CTF on Tryhackme

Link : https://tryhackme.com/room/agentt

Enumeration:
We beging our enumeration with Nmap

└─$ nmap 10.10.197.199 -sV -sC 

Starting Nmap 7.93 ( https://nmap.org )

PORT  STATE SERVICE VERSION

80/tcp open  http    PHP cli server 5.5 or later (PHP 8.1.0-dev)

 |_http-title:  Admin Dashboard

We see that the only port running is 80, visiting the website we can see an admin dashboard template and that the server is running PHP 8.1.0

Now time for Vulnerabilty hunting
Heading over to https://www.exploit-db.com we find that PHP 8.1.0 is vulnerable to RCE by changing our user agent

CVE LINK: https://www.exploit-db.com/exploits/49933

We now download this using wget or the download icon to our linux machine and run the program with python3

python3 49933

The script asks us for the host URL Enter the full host url: 

 http://10.10.89.136

Here we get a shell on the target machine, now we can search for a flag

find / -type f -name "flag.txt"

We are given a location for the flag and we simply need to cat it

cat <flag_location>

There you'll see your flag!
