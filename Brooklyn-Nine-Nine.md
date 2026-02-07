First we'll start with an Nmap scan on the target machine:

nmap -sC -sV -v < machine-ip >

Here, We can see that there are 3 open ports:

21:ftp

22:ssh

80:http

Here, if you look closely we get interesting results for ftp, it shows that we can login to ftp as anonymous.Also we can see that it has a text file named “note_to_jake.txt”.

So, let’s login to ftp using “anonymous” and we'll leave the password as blank. Here, we can find the text file. Now let's Download this txt file using “get” command.


Once we have downloaded note_to_jake.txt. let’s see what it has for us:

contents of note_to_jake.txt

it's from Amy suggesting jake to change his password!

Okay. We can guess that jake is a user of this machine and he is using weak password. :)

So, From our nmap results we know that ssh(port 22) is open. Let’s try bruteforcing ssh using Hydra. We will try to bruteforce user “jake” using this command:

hydra -l jake -P /usr/share/wordlists/rockyou.txt <machine-ip> ssh -t 4

Great! We found jake’s password.

Now, Let’s use this password and login into jake's account using :

ssh jake@< machine-ip >

And we are in!!

Looking at his directory there was nothing much.


After looking at /home directory we can see that there are total three users.


After looking at holt’s home directory found user.txt. Which contains user flag :)


Now, let’s try to escalate our privileges. Let’s see if we have authority to run any commands of root using:

sudo -l

We can see that we can run "less" command as root. Nice! We can leverage this to get a root shell using this command:

sudo less /etc/profile

!/bin/sh 

Awesome! We are root. Now let’s get the root flag.

1st we'll use ls command to list the files of this root directory.

Hey we found it! it's a root.txt file.

Now simply use cat command to get the root flag!!

