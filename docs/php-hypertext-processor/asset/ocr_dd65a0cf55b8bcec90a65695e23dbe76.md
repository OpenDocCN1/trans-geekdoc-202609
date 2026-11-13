Search for the word DocumentRoot (which should appear twice), and change both paths to the directory you want to serve files out of (in our case, /home/httpd). We recommend a home directory rather than the default /usr/local/apache/htdocs because it is more secure, but it doesn.t have to be in a home directory. You will keep all your PHP files in this directory.

+   Add at least one PHP extension directive, as shown in the first line of code that follows. In the second line, we.ve also added a second handler to have all HTML files parsed as PHP
+   
+   ```
+   AddType application/x-httpd-php .php
+   AddType application/x-httpd-php .html
+   ```

+   Restart your server. Every time you change your H T T P configuration or php.ini files, you must stop and start your server again.
+   
+   ```
+   cd ../bin
+   ./apachectl start
+   ```

+   Set the document root directory permissions to world-executable. The actual PHP files in the directory need only be world-readable (644). If necessary, replace /home/httpd with your document root below:
+   
+   ```
+   chmod 755 /home/httpd/html/php
+   ```

+   Open a text editor. Type: <?php phpinfo(); ?>. Save this file in your Web server's document root as info.php.

+   Start any Web browser and browse the file. You must always use an HTTP request (http://www.testdomain.com/info.php or http://localhost/info.php or http://127.0.0.1/info.php) rather than a filename (/home/httpd/info.php) for the file to be parsed correctly

You should see a long table of information about your new PHP installation message Congratulations!

# # PHP Installation on Mac OS X with Apache

Mac users have the choice of either a binary or a source installation. In fact, your OS X probably came with Apache and PHP preinstalled. This is likely to be quite an old build, and it probably lacks many of the less common extensions.

However, if all you want is a quick Apache + PHP + MySQL/PostgreSQL setup on your laptop, this is certainly the easiest way to fly. All you need to do is edit your Apache configuration file and turn on the Web server.

So just follow the steps given below:

+   Open the Apache config file in a text editor as root.
+   
+   ```
+   sudo open -a TextEdit /etc/httpd/httpd.conf
+   ```