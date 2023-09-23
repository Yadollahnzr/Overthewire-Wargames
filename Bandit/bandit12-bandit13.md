# Bandit Level 12 → Level 13

## Level Goal

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

> Commands you may need to solve this level: grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file

> Helpful Reading Material: [Hex dump on Wikipedia](https://en.wikipedia.org/wiki/Hex_dump)

## Solution

This level is about compression. There is different ways to compress a file in linux. I don't want discuss about this ways because this solution is long. You must multiple decompress a file. Let's start.

Connect to the server.
```

ssh bandit12@bandit.labs.overthewire.org -p 2220 

```

In home directory there is a file with 'data.txt' name.

```

bandit12@bandit:~$ ls
data.txt

```

In home directory you don't have permission to make directories or files. For this purpose make a temporary directory and copy ' data.txt ' to this directory and continue.
```

bandit12@bandit:~$ mktemp -d
/tmp/tmp.KAl9JXPxn4
bandit12@bandit:~$ cp data.txt /tmp/tmp.KAl9JXPxn4

```
Now change your current directory and go to temp directory that you created.
```

bandit12@bandit:~$ cd /tmp/tmp.KAl9JXPxn4
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$

```
In this directory you must see data.txt file.

```
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ ls
data.txt

```

You know that 'data.txt' is hex dump. In computing, a hex dump is a hexadecimal view (on screen or paper) of computer data, from memory or from a computer file or storage device. To reverse the hex dump use ` xxd -r `.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ xxd -r data.txt > data
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ ls
data  data.txt

```

` file ` determine type of file. Now use this command to know type of ' data ' file.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ file data
data: gzip compressed data, was "data2.bin", last modified: Sun Apr 23 18:04:23 2023, max compression, from Unix, original size modulo 2^32 581

```

As you see 'data' is gzip compressed. To decompress this file you must change the suffix of 'data' file to 'gz'. Then for decompress use ` gzip -d 'filename' ` command.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ mv data data.gz
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ gzip -d data.gz
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ ls
data  data.txt

```

At above first change 'data' filename to 'data.gz' and after decompressing the results name is 'data'.

Now again use ` file ` to get file type.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ file data
data: bzip2 compressed data, block size = 900k

```

Now the 'data' type is bzip2 compressed. For decompress use below command.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ bzip2 -d data
bzip2: Can't guess original name for data -- using data.out
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ ls
data.out  data.txt

```

The result of this operation is 'data.out'. Again use ` file `.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ file data.out
data.out: gzip compressed data, was "data4.bin", last modified: Sun Apr 23 18:04:23 2023, max compression, from Unix, original size modulo 2^32 20480

```
The type of this file is gzip. Like before first change the suffix and then decompress file.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ mv data.out data.gz
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ gzip -d data.gz
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ ls
data  data.txt
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ file data
data: POSIX tar archive (GNU)

```
After decompressing by ` gzip `, used ` file ` to determine file type.

In this case we have a new compression way. Tar is a very powerful and useful tool. for decompress or in this case extract tar file you must use ` -x -v -f ` switches with ` tar `. ` -x ` is for extract. ` -v ` is vebose and ` -f ` means file.(look at manpage)

For extract a tar file, suffix must be tar. so first rename the 'data' to 'data.tar' and then extract that.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ mv data data.tar
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ ls
data.tar  data.txt
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ tar -xvf data.tar
data5.bin
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ file data5.bin
data5.bin: POSIX tar archive (GNU)

```

The result is another tar file. You must repeat this commands for 'data5.bin'.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ mv data5.bin data5.tar
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ tar -xvf data5.tar
data6.bin
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k

```

'data6.bin' is bzip2 file that spoken above. So you can decompress this file.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ bzip2 -d data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ file data6.bin.out
data6.bin.out: POSIX tar archive (GNU)

```

Again we faced with another tar file. As above repeat steps to extract this file.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ mv data6.bin.out data6.tar
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ tar -xvf data6.tar
data8.bin
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Sun Apr 23 18:04:23 2023, max compression, from Unix, original size modulo 2^32 49

```

Now you must decompress a gzip file.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ mv data8.bin data8.gz
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ gzip -d data8.gz
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ ls
data5.tar  data6.tar  data8  data.tar  data.txt
bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ file data8
data8: ASCII text

```

You get a ASCII text file. Now you can read this file.

```

bandit12@bandit:/tmp/tmp.KAl9JXPxn4$ cat data8
The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

```

You get the password.

