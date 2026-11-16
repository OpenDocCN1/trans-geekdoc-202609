```
./configure --exec-prefix=/usr \
--localstatedir=/var \
--mandir=/usr/share/man \
--libexecdir=/System/Library/Apache/Modules \
--iconsdir=/System/Library/Apache/Icons \
--includedir=/System/Library/Frameworks/Apache.framework/Versions/1.3/Headers \
--enable-shared=max \
--enable-module=most \
--target=apache
```

Make sure that `--includedir=.../1.3/Headers \` is all on one line.

# Compilling Apache

If all goes well with the configuration, you can now compile Apache:

```
make
```

If this succeeds, you can install Apache:

```
make install
```

At this point, you may not have a working Apache, since your old httpd.conf file was probably not overwritten, and it probably is still trying to load the old PHP which may or may not have been configured and compiled to work with your new version of Apache.

You can edit httpd.conf and comment out (do not delete) any lines mentioning php and then stop and start Apache to test Apache:

```
apachectl stop
apachectl start
```

You may need to change into Apache's bin directory before issuing these commands, or use bin/apachectl.

> Due to an issue with the Mac OS X GUI, it is not recommended that Apache be started through the use of the System Preferences | Sharing applet. Although Apache will start when web sharing is enabled, OS X will not allow you to turn Apache off once it has started. For this reason it is recommended that Apache only be started and stopped from a terminal window by calling apachectl.

After issuing an apachectl start command, you can check to make sure that Apache really did start by searching for the server process httpd in the process list, by using a combination of the ps and grep commands as shown, or by searching for httpd in the Mac OS X process viewer:

```
ps -A | grep httpd
620 nobody      00:00:00 httpd
621 nobody      00:00:00 httpd
622 nobody      00:00:00 httpd
```