# Bandit Level 13 → Level 14

## Level Goal

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

> Commands you may need to solve this level: ssh, telnet, nc, openssl, s_client, nmap

> Helpful Reading Material: [SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

## Solution

For connecting to the server use below command.
```bash

ssh bandit13@bandit.labs.overthewire.org -p 2220

```

After login, If you check home directory you see there is a file with " sshkey.private " name. This file is a private key that can be used to connect to a remote server (For more information see " Helpful Reading Material ").

` ssh ` has a switch to determine identity file like private key and that switch is ` -i `. So you must use this switch to connect to the localhost as " bandit14 ".

```bash

bandit13@bandit:~$ ssh bandit14@localhost -p 2220 -i sshkey.private
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes

```

After execute above command you must answer " Are you sure ... " with yes to continue connecting.

After that you are in " bandit14 " home directory and you have " bandit14 " permissions. So you can read " /etc/bandit_pass/bandit14 " to gain the password.

```bash

bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

```
