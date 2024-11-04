
> Someone is trying to hack my server, the username and password for it is ctfuser. They stole my important text file, please get it back for me.

```bash
ctfuser@dd73dde9b56a:~$ cat ~/.logs/auth.log
Sep 10 11:07:02 sshd[12345]: Accepted password for ctfuser from 192.168.1.10 port 2200 ssh2
Sep 10 11:07:16 sshd[12345]: Accepted password for ctfuser from 192.168.1.10 port 2200 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:07:40 sshd[12345]: Failed password for invalid user admin from port 2121 ssh2
Sep 10 11:09:20 sshd[12345]: Accepted password for ctfuser from 192.168.1.10 port 2200 ssh2
Sep 10 11:09:23 sshd[12345]: Accepted password for ctfuser from 192.168.1.10 port 2200 ssh2
Sep 10 11:09:33 sshd[12345]: Accepted password for ctfuser from 192.168.1.10 port 2200 ssh2
Sep 10 11:09:59 sshd[12345]: Accepted password for ctfuser from 192.168.1.10 port 2200 ssh2
```

It was a FTP server running on challenges.ctf.sikt.no 2121, with no username or password. The flag was in the file 'flag.txt'.

It was hard to guess that the server was on challanges.ctf.sikt.no. I actually ended monitoring and decoding the data of `/proc/tcp/` (basically made netstat in python) until I saw a connection to the server and used Python to connect to the server and view the file. It turns out that the server was open to the public and you could just connect to it with a ftp client from your pc.

> Flag: SiktCTF{WHo_is_TH3_Re4L_HaCk3R?}