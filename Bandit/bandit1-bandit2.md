# Bandit Level 1 → Level 2

## Level Goal
The password for the next level is stored in a file called - located in the home directory

> Commands you may need to solve this level: ls , cd , cat , file , du , find

> Helpful Reading Material: [Google Search for “dashed filename”](https://www.google.com/search?q=dashed+filename) , [Advanced Bash-scripting Guide - Chapter 3 - Special Characters](http://tldp.org/LDP/abs/html/special-chars.html)

## Solution

First you must connect to the game server with user bandit1 and the password that find in the previous level.
```

ssh bandit1@bandit.labs.overthewire.org -p 2220 

```
If you use ` ls ` command see that there is a file with - name.

```

bandit1@bandit:~$ ls
-

```
You know that the password is in that file. If try to read this file with ` cat ` command as below you get nothing.
```

bandit1@bandit:~$ cat -

```
For read a dashed filename file use " ./ " before the filename.

```

bandit1@bandit:~$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

```
Here you are, You get the password.
