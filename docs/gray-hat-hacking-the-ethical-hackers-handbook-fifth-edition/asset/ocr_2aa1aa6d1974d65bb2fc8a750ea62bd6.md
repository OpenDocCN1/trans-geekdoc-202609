```
```
root@kali:~/DAP-1320/fmk/rootfs# find . -type f -perm /u+x -name "*httpd*" -o
-name "*cgi*" -o -name "*nginx*"
<truncated for brevity>
①./sbin/lighttpd
./sbin/lighttpd-angel
./etc/conf.d/cgi.conf
./bin/cgi
root@kali:~/DAP-1320/fmk/rootfs# find . -name *.conf
②./etc/lighttpd.conf
./etc/conf.d/mime.conf
./etc/conf.d/cgi.conf
./etc/conf.d/auth_base.conf
./etc/conf.d/expire.conf
./etc/conf.d/auth.conf
./etc/conf.d/dirlisting.conf
./etc/conf.d/graph_auth.conf
./etc/conf.d/access_log.conf
./etc/modules.conf
./etc/host.conf
./etc/resolv.conf
②./etc/lighttpd_base.conf
root@kali:~/DAP-1320/fmk/rootfs# cat etc/lighttpd_base.conf
###############################################################################
## /etc/lighttpd/lighttpd.conf
## check /etc/lighttpd/conf.d/*.conf for the configuration of modules.
```
```