These lines can be added virtually anywhere, but should be placed near all the other AddType and AddHandler directives in the file in order to keep things clean. Note that PHP should already have edited this file to add the following line:

```
LoadModule php6_module lib/apache/libphp6.so
```

Confirm that the preceding line is already in your httpd.conf file. If not, add it.

# Testing Your Installation

All that remains is to test your installation. Start Apache using the following syntax:

```
# /usr/local/apache/bin/apachectl start
```

Now create a file in /usr/local/apache/htdocs called test.php containing the following code:

```
<?php
phpinfo();
?>
```

Save it and, in your workstation's Web browser, point it to the IP address of your UNIX machine,
followed by /phpinfo.php. For example, if your server is 192.168.1.1, point it to
http://192.168.1.1/phpinfo.php. You should see a screen showing the full details of your PHP
installation.

If so, congratulations. Your PHP installation has been successful! You will probably want to create virtual
server entries for each project that you work on, however. Much more information on this can be found
in Chapter 21.

# When Windows Is Needed

Scenarios do crop up for which you will simply have to use Windows. The most classic example is for
the installation of a closed system onto a large company's IT infrastructure, which is already Windows-
based, and management has resolutely refused to install a UNIX server.

With some adaptation, the examples in this book will all still work just fine. The following pointers may
help you transfer your PHP from UNIX to Windows.

# Changing Paths

Don't forget that paths on Windows look very different from paths on UNIX. References to paths
such as /data/res/1230.jpg on disk need to be changed to a Windows equivalent, such as
C:\\ data\\ res\\ 1230.jpg.

PHP is kind and allows you to keep the slashes oblique (/). If you avoid drive letters by using relative
paths, you may be able to keep your application more portable.