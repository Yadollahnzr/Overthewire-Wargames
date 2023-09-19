# Leviathan0 -> Leviathan1

This level is the first level of Leviathan game. You must connect to the server and find the password without any addition informations about where is the password.

## Sulotion

To connect to the server you can use below command.
```

ssh leviathan0@leviathan.labs.overthewire.org -p 2223

```

After login, you must start the searching. We don't have any information about the location of password; So take a list of existing files with below command.
```

ls -la

```
If you use ` ls ` command without ` -la ` switch, you get nothing. Because the files are hidden, you must use ` -a ` switch. ` -l ` switch is long listing format and give you extra informations. The informations is about permissions, owner and group, size of files and date of create and modified.

Use this command give you below output:
```

leviathan0@gibson:~$ ls -la
total 24
drwxr-xr-x  3 root       root       4096 Apr 23 18:04 .
drwxr-xr-x 83 root       root       4096 Apr 23 18:06 ..
drwxr-x---  2 leviathan1 leviathan0 4096 Apr 23 18:04 .backup
-rw-r--r--  1 root       root        220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root       root       3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root       root        807 Jan  6  2022 .profile

```

" .backup " directory is suspicious. The owner of this directory is ' leviathan1 ' and group is ' leviathan0 '. So you must change directory and go to this directory and continue the shearching.
```

leviathan0@gibson:~$ cd ./.backup/
leviathan0@gibson:~/.backup$

```
Now take a list of files like last time.
```

leviathan0@gibson:~/.backup$ ls -la
total 140
drwxr-x--- 2 leviathan1 leviathan0   4096 Apr 23 18:04 .
drwxr-xr-x 3 root       root         4096 Apr 23 18:04 ..
-rw-r----- 1 leviathan1 leviathan0 133259 Apr 23 18:04 bookmarks.html

```
You see. There is a file with name ' bookmarks.html ', the owner is leviathan1 and group is ' leviathan0 '. This file is suspicious. If you use ` cat ` to read this file, you see, this file is very large and reading this file is take to much time. 

Let's try our luck. use ` cat ` with ` grep ` in shape of below.
```

leviathan0@gibson:~/.backup$ cat bookmarks.html | grep password
<DT><A HREF="http://leviathan.labs.overthewire.org/passwordus.html | This will be fixed later, the password for leviathan1 is PPIfmI1qsA" ADD_DATE="1155384634" LAST_CHARSET="ISO-8859-1" ID="rdf:#$2wIU71">password to leviathan1</A>

```
Our luck worked. Password is found.  "the password for leviathan1 is PPIfmI1qsA."
