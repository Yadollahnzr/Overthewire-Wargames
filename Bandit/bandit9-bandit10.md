# Bandit Level 9 → Level 10

## Level Goal

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

> Commands you may need to solve this level: grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## Solution

For first step, connect to the server.
```

ssh bandit9@bandit.labs.overthewire.org -p 2220

```

You know that the password is in the data.txt.
```

bandit9@bandit:~$ ls -la
total 40
drwxr-xr-x  2 root     root     4096 Apr 23 18:04 .
drwxr-xr-x 70 root     root     4096 Apr 23 18:05 ..
-rw-r--r--  1 root     root      220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root     root     3771 Jan  6  2022 .bashrc
-rw-r-----  1 bandit10 bandit9 19379 Apr 23 18:04 data.txt
-rw-r--r--  1 root     root      807 Jan  6  2022 .profile

```

` strings ` command print the sequences of printable characters in files. In ' data.txt ' there is human-readable strings. For print them you can use ` strings `.
```

bandit9@bandit:~$ strings data.txt

```

In the result of this command you get some strings that printable.

The password is preceded by several ' = '. So you can use ` grep ` to gain password.
```

bandit9@bandit:~$ strings data.txt | grep ====
4========== the#
========== password
========== is
========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

```
Now you find the password.

