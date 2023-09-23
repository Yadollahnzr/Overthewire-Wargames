# Leviathan Level 1 → Level 2

## Solution

To connect to the server use below command.
```

ssh leviathan1@leviathan.labs.overthewire.org -p 2223

```

After connect, first step is use ` ls ` to get existing files.

```

leviathan1@gibson:~$ ls -la
total 36
drwxr-xr-x  2 root       root        4096 Apr 23 18:04 .
drwxr-xr-x 83 root       root        4096 Apr 23 18:06 ..
-rw-r--r--  1 root       root         220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root       root        3771 Jan  6  2022 .bashrc
-r-sr-x---  1 leviathan2 leviathan1 15072 Apr 23 18:04 check
-rw-r--r--  1 root       root         807 Jan  6  2022 .profile

```
' check ' file is suspicious. Because the owner is leviathan2 and group is leviathan1.

Let's check the check file.
```

leviathan1@gibson:~$ ./check
password: PPIfmI1qsA
Wrong password, Good Bye ...

```
For example, i think that the password of the check file is the same previous level password but it's not true. So we must search for check password.

` ltrace ` is a program that simply runs the specified command until it exits.  It intercepts and records the dynamic library calls which are called by the executed process and the signals which are received by that process. It can also intercept and print the system calls executed by the program.

` ltrace ` shows parameters of invoked functions and system calls. To determine what arguments each function has, it needs external declaration of function prototypes.
If you run check file by ltrace get following result.
```

leviathan1@gibson:~$ ltrace ./check
__libc_start_main(0x80491e6, 1, 0xffffd5f4, 0 <unfinished ...>
printf("password: ")                                                                                                              = 10
getchar(0xf7fbe4a0, 0xf7fd6f80, 0x786573, 0x646f67password: PPIfmI1qsA
)                                                                               = 80
getchar(0xf7fbe4a0, 0xf7fd6f50, 0x786573, 0x646f67)                                                                               = 80
getchar(0xf7fbe4a0, 0xf7fd5050, 0x786573, 0x646f67)                                                                               = 73
strcmp("PPI", "sex")                                                                                                              = -1
puts("Wrong password, Good Bye ..."Wrong password, Good Bye ...
)                                                                                              = 29
+++ exited (status 0) +++

```
There is ` strcmp ` function in the result. This function is compare input strings. Maybe it's parameters the password of check file. As you see parameters are ' PPI ' and ' sex '. ' PPI ' is first three characters that i input for passowrd. ' sex ' must be the password. 

Let's try.

```

leviathan1@gibson:~$ ./check
password: sex
$ whoami
leviathan2

```

After entring the password you get shell. Run ` whoami ` to find out your current username. If it's " leviathan2 ", you can continue.

You know the password of leviathan is in " /etc/leviathan_pass/leviathan# " that ' # ' is determine the user number that you want it's password.

Final step is use ` cat ` to reading password file.

```

$ cat /etc/leviathan_pass/leviathan2
mEh5PNl10e

```

