
# Bandit Level 0

## Level Goal
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.


> Commands you may need to solve this level: ssh

> Helpful Reading Material: 
>	[Secure Shell (SSH) on Wikipedia](https://en.wikipedia.org/wiki/Secure_Shell) , 
>	[How to use SSH on wikiHow](https://www.wikihow.com/Use-SSH)


## Solution
    
For connect to a remote server we can use ssh.The Secure Shell Protocol (SSH) is a cryptographic network protocol for operating network services securely over an unsecured network. Its most notable applications are remote login and command-line execution.
### usage:
To connect to a server via ssh we must have username and password of that user we want to login with the user identity and know the server IP or domain. For this level we want to connect to bandit.labs.overthewire.org on port 2220 and by bandit0 for username and bandit0 for password. Below command do this for us.
```bash

ssh bandit0@bandit.labs.overthewire.org -p 2220

```
Before @ wrote the username that wants to connect by it's identity and after @ determined the server.
-p switch determine specific port to connect to the server. Default port for ssh connection is 22 and if we don't determine port number by -p switch, ssh use it's defult port to establish connection.
After enter above command on terminal we see this massages.

```

                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit0@bandit.labs.overthewire.org's password:

```
Now you must enter the password of user. For this case ` bandit0 `. If you have used terminal and command line you know that when you enter the password it doesn't shown. So it doesn't matter and enter password only ones.
If password was correct your username must changed. For this case ` bandit0@bandit:~$ ` must be your identity.
To exit any ssh connection use ` exit ` command.
