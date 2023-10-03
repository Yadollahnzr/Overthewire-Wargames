# Bandit Level 7 → Level 8

## Level Goal
The password for the next level is stored in the file data.txt next to the word millionth

> Commands you may need to solve this level: man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## Solution
First connect to the sereve.
```

ssh bandit7@bandit.labs.overthewire.org -p 2220

```

Use ls command.
```

bandit7@bandit:~$ ls
data.txt

```
If you try to read ' data.txt ', you see this is a large file and you can't find the password easily.

You must use ` grep ` command. This command is find lines that matches to given pattern. Look man page to more information.
```

bandit7@bandit:~$ cat data.txt | grep millionth
millionth       TESKZC0XvTetK0S9xNwm25STk5iWrBvP

```
Because in the level goal said the password is next to the ' millionth ', the pattern that given to the ` grep ` is this word.

Now you find the password.
