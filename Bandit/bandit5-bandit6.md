# Bandit Level 5 → Level 6
## Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable

> Commands you may need to solve this level: ls , cd , cat , file , du , find

## Sulotion
For connecting to the server use below command.
```

ssh bandit5@bandit.labs.overthewire.org -p 2220

```
You know the password is somewhere in ' inhere ' directory. So You must should change current directory.
```

bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$

```
If you use ` ls ` command, you see there is lots of direcotries and in each directory there is lot's of files. So it is impossible to read each file to find desired file.
```
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere02  maybehere04  maybehere06  maybehere08  maybehere10  maybehere12  maybehere14  maybehere16  maybehere18
maybehere01  maybehere03  maybehere05  maybehere07  maybehere09  maybehere11  maybehere13  maybehere15  maybehere17  maybehere19
bandit5@bandit:~/inhere$ ls -la maybehere00
total 72
drwxr-x---  2 root bandit5 4096 Apr 23 18:04 .
drwxr-x--- 22 root bandit5 4096 Apr 23 18:04 ..
-rwxr-x---  1 root bandit5 1039 Apr 23 18:04 -file1
-rwxr-x---  1 root bandit5  551 Apr 23 18:04 .file1
-rw-r-----  1 root bandit5 9388 Apr 23 18:04 -file2
-rw-r-----  1 root bandit5 7836 Apr 23 18:04 .file2
-rwxr-x---  1 root bandit5 7378 Apr 23 18:04 -file3
-rwxr-x---  1 root bandit5 4802 Apr 23 18:04 .file3
-rwxr-x---  1 root bandit5 6118 Apr 23 18:04 spaces file1
-rw-r-----  1 root bandit5 6850 Apr 23 18:04 spaces file2
-rwxr-x---  1 root bandit5 1915 Apr 23 18:04 spaces file3

```
In top commands you see ` -la ` switch is used with ` ls ` command. ` -a ` is list all files in addition hidden files. ` -l ` is long list format and print extra information about each file.

` find ` command is used to search for specific files in a directory hierarchy.
It has different switches. At this moment you need only ` -type `, ` -size ` and ` -executable `.

` -type ` is for determine type of the file you search and each type has specific character to use with this switch. You can use ` man find ` to see this character but in this level we need ' f ' to determine a humanreadable file. 

` -size ` is for determine the size of file(s) that you search. File uses less than, more than or exactly n units of space, rounding up. Different suffixes can use to determine size( see man page of ` find ` ). In this case you must use 'c' suffix to determin bytes.

` -executable ` switch is matches files which are executable. In this this case you must search file that is not executable. For approuch this you need ' ! ' to opposite the result of ` -executable `.
```

bandit5@bandit:~/inhere$ find . -type f -size 1033c ! -executable 
./maybehere07/.file2

```
The file that you search is " ./maybehere07/.file2 ". You need read this file to find the password.

```

bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

```

