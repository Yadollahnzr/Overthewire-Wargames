# Bandit Level 8 → Level 9
## Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

> Commands you may need to solve this level: grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

> Helpful Reading Material: [Piping and Redirection](https://ryanstutorials.net/linuxtutorial/piping.php)

## Solution

At first you must connect to the server.
```

ssh bandit8@bandit.labs.overthewire.org -p 2220

```

There is a data.txt file in home directory.
```

bandit8@bandit:~$ ls
data.txt

```
This file is large and reading this file for find the password is take to much time. So you need ` sort ` and ` uniq ` command. ` Sort ` command sort lines of the file alphabetically. ` uniq ` report or omit repeated lines. It has multiple switches. At this time you need ` -u ` switch to determine that you want uniq line(s).

```

bandit8@bandit:~$ sort data.txt | uniq -u
EN632PlfYiZbn3PhVK3XOGSlNInNE00t

```
The ` uniq ` command requires that the file to omit repeated lines is sorted.


