# Getting information from Apache

You can use options with the httpd server to obtain information about Apache. For instance, you can find out what version of Apache is installed by changing to the directory with httpd and typing

```
httpd -v
```

Or, probably, ./httpd -v. You can find out what modules are installed with Apache by typing the following:

```
httpd -l
```

To see all the options that are available, type the following:

```
httpd -h
```

# Restarting Apache

Whenever you change the configuration file, the new directives take effect the next time Apache starts. If Apache is shut down when you make the changes, you can start Apache as described earlier in “Starting Apache.” However, if Apache is running, you can’t use start to restart it. Using start results in an error message saying that Apache is already running. You can use the following command to restart Apache when it’s currently running:

```
/usr/local/apache2/bin/apachectl restart
```

Although the restart command usually works, sometimes it doesn’t. If you restart Apache and the new settings don’t seem to be in effect, try stopping Apache and starting it again. Sometimes this solves the problem.

# Stopping Apache

To stop Apache, use the following command:

```
/usr/local/apache/bin/apachectl stop
```

You can check to see that Apache is stopped by checking the processes that are running on your computer by using the following command:

```
ps -A
```

The output from ps should not include any httpd processes.

# On Windows

You can install Apache on almost any version of Windows, although Windows NT/2000/XP are preferred.