+   Tell your Apache server where you want to serve files from and what extension(s) you want to identify PHP files (.php is the standard, but you can use .html, .phtml, or whatever you want). Go to your HTTP configuration files (C:\Program Files\Apache Group\Apache\conf or whatever your path is), and open httpd.conf with a text editor. Search for the word DocumentRoot (which should appear twice) and change both paths to the directory you want to serve files out of. (The default is C:\Program Files\Apache Group\Apache\htdocs.). Add at least one PHP extension directive as shown in the first line of the following code:

```
LoadModule php5_module modules/php5apache.dll
AddType application/x-httpd-php .php .phtml
```

+   You may also need to add the following line:

```
AddModule mod_php5.c
```

+   Stop and restart the WWW service. Go to the Start menu -> Settings -> Control Panel -> Services. Scroll down the list to IIS Admin Service. Select it and click Stop. After it stops, select World Wide Web Publishing Service and click Start. Stopping and restarting the service from within Internet Service Manager will not suffice. Since this is Windows, you may also wish to reboot.

+   Open a text editor. Type: <?php phpinfo(); ?>. Save this file in your Web server's document root as info.php.

+   Start any Web browser and browse the file.you must always use an HTTP request (http://www.testdomain.com/info.php or http://localhost/info.php or http://127.0.0.1/info.php) rather than a filename (/home/httpd/info.php) for the file to be parsed correctly

You should see a long table of information about your new PHP installation message Congratulations!

# Apache Configuration

If you are using Apache as a Web Server, then this section will guide you to edit Apache Configuration Files.

# PHP.INI File Configuration

The PHP configuration file, php.ini, is the final and most immediate way to affect PHP's functionality.

Just Check it here: PHP.INI File Configuration

# Windows IIS Configuration

To configure IIS on your Windows machine you can refer your IIS Reference Manual shipped along with IIS.