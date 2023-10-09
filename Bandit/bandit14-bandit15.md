# Bandit Level 14 → Level 15

## Level Goal

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

> Commands you may need to solve this level: ssh, telnet, nc, openssl, s_client, nmap

> Helpful Reading Material

    + [How the Internet works in 5 minutes (YouTube) (Not completely accurate, but good enough for beginners)](https://www.youtube.com/watch?v=7_LPdttKXPc)
    + [IP Addresses](http://computer.howstuffworks.com/web-server5.htm)
    + [IP Address on Wikipedia](https://en.wikipedia.org/wiki/IP_address)
    + [Localhost on Wikipedia](https://en.wikipedia.org/wiki/Localhost)
    + [Ports](http://computer.howstuffworks.com/web-server8.htm)
    + [Port (computer networking) on Wikipedia](https://en.wikipedia.org/wiki/Port_(computer_networking))


## Solution

" netcat "  is a simple unix utility which reads and writes data across network connections, using TCP or UDP protocol. It is designed to be a reliable "back-end" tool that can be used directly or easily driven by other programs and scripts. At the same time, it is a feature-rich network debugging and exploration tool, since it can create almost any kind of connection you would need and has several interesting built-in capabilities. 

Netcat, or "nc" as the actual program is named, should have been supplied long ago as another one of those cryptic but standard Unix tools. In the simplest usage, "nc host port" creates a TCP connection to the given port on the given target host. Your standard input is then sent to the host, and anything that comes back across the connection is sent to your standard output. This continues indefinitely, until the network side of the connection shuts down. Note that this behavior is different from most other applications which shut everything down and exit after an end-of-file on the standard input.

In this level you must use netcat and send the password of previous level to the 30000 port of localhost and then the server give you the password of next level. Let's start it.


First you need to connect to the server via ssh.

```bash

ssh bandit14@bandit.labs.overthewire.org -p 2220

```

Now you must use ` nc ` to create a connection on localhost port 30000.

```bash

bandit14@bandit:~$ nc localhost 30000


```

At last you must send the previous level password to get the next password.

```bash

bandit14@bandit:~$ nc localhost 30000
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

```


