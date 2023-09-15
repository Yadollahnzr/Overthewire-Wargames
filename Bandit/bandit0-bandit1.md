# Bandit Level 0 → Level 1

## Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

> Commands you may need to solve this level: ls , cd , cat , file , du , find

## Sulotion
You need first connect to the game server. This concept discussed in [bandit0.md](Bandit/bandit0.md). You can use below command to connect to the server.

```

ssh bandit0@bandit.labs.overthewire.ort -p 2220

```
The password for user bandit0 is bandit0. Now you have access to run commandes remotely on the server.
First step for find the next level password is use ` ls ` command. After enter that command you see there is a file with readme name.
```

bandit0@bandit:~$ ls
readme

```
We know that the password is in the readme file. So use ` cat ` command to read the readme file.
```
bandit0@bandit:~$ cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL

```
Now we have the next level password.

for more information about ` ls ` and ` cat ` command use ` man ls ` and ` man cat ` to access the manual page of this commands.
