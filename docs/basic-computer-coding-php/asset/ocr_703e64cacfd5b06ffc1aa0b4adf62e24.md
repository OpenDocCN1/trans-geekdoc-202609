# Basic Computer Coding: PHP

+   - Open a text editor. Type: <?php phpinfo(); ?> Save this file in your Web server's document root as info.php.

+   - Start any Web browser and browse the file.you must always use an HTTP request (http://www.testdomain.com/info.php or http://localhost/info.php or http://127.0.0.1/info.php) rather than a filename (/home/httpd/info.php) for the file to be parsed correctly

You should see a long table of information about your PHP installation message Congratulations!

# PHP Installation on Mac OS X with Apache

Mac users have the choice of either a binary or a source installation. In fact, your OS X probably came with Apache and PHP preinstalled. This is likely to be quite an old build, and it probably lacks many of the less common extensions.

However, if all you want is a quick Apache + PHP + MySQL/PostgreSQL setup on your laptop, this is certainly the easiest way to fly. All you need to do is edit your Apache configuration file and turn on the Web server.

So just follow the following steps

+   - Open the Apache config file in a text editor as root. sudo open -a TextEdit /etc/httpd/httpd.conf

+   - Edit the file. Uncomment the following lines - LoadModule php5_module

```
AddModule mod_php5.c
AddType application/x-httpd-php .php
```

+   - You may also want to uncomment the <Directory /home/* Sites> block or otherwise tell Apache which directory to use out of.

+   - Restart the Web server sudo apachectl graceful

+   - Open a text editor. Type: <?php phpinfo(); ?> Save this file in your Web server's document root as info.php.