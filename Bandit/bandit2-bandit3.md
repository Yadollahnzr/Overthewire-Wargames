# Bandit Level 2 → Level 3
## Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory

> Commands you may need to solve this level: ls , cd , cat , file , du , find

> Helpful Reading Material: [Google Search for “spaces in filename”](https://www.google.com/search?q=spaces+in+filename)

## Sulotion
First using below command to connect to the game server. 
```

ssh bandit2@bandit.labs.overthewire.org -p 2220

```
Now use ` ls ` command.

```

bandit2@bandit:~$ ls
spaces in this filename

```
To read a file that inside it's name has spaces must use double quotation. If use cat command as ` cat spaces in this filename ` shell think you want to cat multiple files and don't know the spaces in this filename is the one filename. So use below code to read the file and get the password.
```

bandit2@bandit:~$ cat "spaces in this filename"
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

```

