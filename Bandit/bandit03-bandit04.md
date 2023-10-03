# Bandit Level 3 → Level 4
## Level Goal
The password for the next level is stored in a hidden file in the inhere directory.

> Commands you may need to solve this level: ls , cd , cat , file , du , find

## Solution
At first you must connect to the game server by bandit3 username.
```

ssh bandit3@bandit.labs.overthewire.org -p 2220

```
After login, now you are is home directory. If use ` ls ` command you see there is a directory that's name is inhere. As stated in level goal, the password is in a hidden file in 'inhere' directory. so need to go to the inhere directory. For this purpose you need use ` cd `. 
```

bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$

```
Now if you use ` ls ` you get nothing. For list hidden files you need to use ' -a ' switch. Using this switch with ` ls ` you can list all available files in the current directory.
```
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -a
.  ..  .hidden

```
Hidden file's name in linux start with ' . '. To ` cat ` '.hidden' file must use as below command.

```

bandit3@bandit:~/inhere$ cat ./.hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

```
You find the next level password.

note: Files '.' and '..' are directories that '.' is current directory and '..' is parent directory.
