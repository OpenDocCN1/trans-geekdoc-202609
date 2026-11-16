We can combine the two files so that all the needed information is together and consolidated by using the unshadow program. This merges the information in the shadow file and the passwd file. Here, you can see a run of unshadow with a captured shadow file and passwd file.

# Using unshadow

```
root@quiche:~# unshadow passwd.local shadow.local
root:$6$ycC28ASuSwMwFkwvikDeKL4VTjgEnYcD.PXG.4uixCikB05jBvE3JjV43nLsfpB1z57qWL
h0SNo1m5fJfyQWEMhLjRv4rR0.:0:0:root:/root:/bin/bash
daemon:*:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:*:2:2:bin:/bin:/usr/sbin/nologin
sys:*:3:3:sys:/dev:/usr/sbin/nologin
sync:*:4:65534:sync:/bin:/bin:sync
games:*:5:60:games:/usr/games:/usr/sbin/nologin
man:*:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:*:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:*:8:8:mail:/var/mail:/usr/sbin/nologin
news:*:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:*:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:*:13:13:proxy:/bin:/usr/sbin/nologin
www-data:*:33:33:www-data:/var/www:/usr/sbin/nologin
backup:*:34:34:backup:/var/backups:/usr/sbin/nologin
list:*:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:*:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:*:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/
nologin
```

As seen, most of the users don't have passwords. The only user with a password here
is the root user. Once you have the two files merged using unshadow, you can run John
against it to acquire the password. John will identify the format of the file and the hash
algorithm used to generate it. This information is stored in the file. The $6$ at the begin-
ning of the password indicates that the password has been hashed using the secure hash
algorithm with 512 bits for the output (SHA-512). What comes after that is the hashed
password that John will be comparing against. John, though, isn't the only way to obtain
passwords from local files.

# Rainbow Tables

For every password tested using John, you have to compute the hash to test against. This
takes time and computational power. With today's processors, the time and computing
power necessary aren't such a big deal other than it adds up. Microseconds per word over
the course of millions of words adds time. It's easier to precompute the hashes before run-
ning your checks. All you need to do then is look up the hash in an index and retrieve the