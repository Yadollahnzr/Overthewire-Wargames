# Bandit Level 11 → Level 12

## Level Goal

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

> Commands you may need to solve this level: grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

> Helpful Reading Material: [Rot13 on Wikipedia](https://en.wikipedia.org/wiki/Rot13)

## Solution

First connect to the server.
```

ssh bandit11@bandit.labs.overthewire.org -p 2220

```
Rotated by 13 means that a-z lowercase and uppercase alphabets are replace with n-za-m order of alphabets.

For reverse this conversion you must use ` tr ` command. See man page of this command for get information about options of this command. In this case we use ` [a-zA-z] [n-za-mZ-NA-M] ` as sequences you want to translate the input text. It means that replace all lowercase and uppercase alphabets (a-zA-Z) with (n-za-m) for lowercase and (N-ZA-M for uppercase).

Now get start. first you must ` cat ` 'data.txt and then use pipeline to send ` cat ` output to the ` tr `.
```

bandit11@bandit:~$ cat data.txt | tr [a-zA-Z] [n-za-mN-ZA-M]
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

```

