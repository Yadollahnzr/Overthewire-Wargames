# Bandit Level 4 → Level 5
## Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

> Commands you may need to solve this leve: ls , cd , cat , file , du , find

## Sulotion
In computing, a **human-readable medium** or **human-readable format** is any encoding of data or information that can be naturally read by humans, resulting in **human-readable data**. It is often encoded as ASCII or Unicode text, rather than as binary data.

**_Now, How can determine file type?_**

The answer is ` file ` command.
` file ` tests each argument in an attempt to classify it.  There are three sets of tests, performed in this order: filesystem tests, magic tests, and language tests.  The first test that succeeds causes the file type to be printed.

### Get start the game:
Like previous levels you must connect to the game server. For this level username is bandit4.
```

ssh bandit4@bandit.labs.overthewire.org -p 2220

```
Next use ` ls ` to find out what things are there.
```

bandit4@bandit:~$ ls
inhere

```
As in level goal said the password is in the inhere directory. So you must change current directory to 'inhere'.
```

bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$

```
After that you should get list of files that are in this directory.
```

bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09

```
As you see in this directory there is 10 files. In this case you can read files one by one but if there was more files, it is impossible to read files one by one. It is spoken that how to find a file is human readable or not. Now with ` file ` command as below we get some output like this:
```

bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: Non-ISO extended-ASCII text, with no line terminators

```
There are three type of files.

1. **'Data'** file type is binary file and not human readable.

1. **'ASCII text'** is what we were looking for. 

1. If file tells you “Non-ISO extended-ASCII text” because it detects that this is:

   - most likely a “text” file from the lack of control characters (byte values 0–31) other than line breaks;
   - “extended-ASCII” because there are characters outside the ASCII range (byte values ≥128);
   - “non-ISO” because there are characters in the 128–159 range (ISO 8859 reserves this range for control characters).

The last step is read the ./-file07 that is you found out it is human readable.
```

bandit4@bandit:~/inhere$ cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

```
Now you hanve next level password.

