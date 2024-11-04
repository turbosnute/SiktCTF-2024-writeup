
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

FTP challenges.ctf.sikt.no 2121. With no username or password. The flag is in the file 'flag.txt'.

> Flag: SiktCTF{WHo_is_TH3_Re4L_HaCk3R?}