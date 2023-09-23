# Bandit Level 10 → Level 11

## Level Goal

The password for the next level is stored in the file data.txt, which contains base64 encoded data

> Commands you may need to solve this level: grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

> Helpful Reading Material[Base64 on Wikipedia](https://en.wikipedia.org/wiki/Base64)

## Solution

In this level you must use base64 decode. 

First connect to the server.
```

ssh bandit10@bandit.labs.overthewire.org -p 2220

```

Use ` ls `.
```

bandit10@bandit:~$ ls -la
total 24
drwxr-xr-x  2 root     root     4096 Apr 23 18:04 .
drwxr-xr-x 70 root     root     4096 Apr 23 18:05 ..
-rw-r--r--  1 root     root      220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root     root     3771 Jan  6  2022 .bashrc
-rw-r-----  1 bandit11 bandit10   69 Apr 23 18:04 data.txt
-rw-r--r--  1 root     root      807 Jan  6  2022 .profile

```

There is data.txt file that is base64 encoded.
```

bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIDZ6UGV6aUxkUjJSS05kTllGTmI2blZDS3pwaGxYSEJNCg==

```

You must decode this file to get the password.

` base64 ` command is used for this purpose. It has ` -d ` switch that use for decode given file. Use this command as below to decode ' data.txt '.
```

bandit10@bandit:~$ base64 -d data.txt
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

```


