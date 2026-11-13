If they support remote access to the MySQL server, you'll want to download a program that lets you connect to, and interact with, the server. This book assumes you've downloaded from http://www.mysql.com/ a binary distribution of MySQL that includes the three client programs (mysql, mysqladmin, and mysqldump). Free packages are available for Windows, Linux and other operating systems. Installation basically consists of finding the three programs and putting them in a convenient place. The rest of the package, which includes the MySQL server, can be freely discarded. If you prefer a more graphical interface, download something like MySQL GUI (also available from http://www.mysql.com). I'd really recommend getting comfortable with the basic client programs first, though, as the commands you use with them will be similar to those you'll include in your PHP scripts to access MySQL databases.

Some less expensive Web hosts these days support neither telnet/SSH access, nor direct access to their MySQL servers. Instead, they provide a management console that allows you to browse and edit your database through your Web browser. Although this is a fairly convenient and not overly restrictive solution, it doesn't help you learn. Instead, I'd recommend the installation of a MySQL server on your own system to help, especially in the next chapter. Once you're comfortable working with your learning server, you can start using the server provided by your Web host with their management console. See the previous sections for instructions on installing MySQL under Windows and Linux.

# # Your First PHP Script

It would be unfair of me to help you get everything installed and not even give you a taste of what a PHP-driven Web page looks like until Chapter 3, so here's a little something to whet your appetite.

Open up your favorite text or HTML editor and create a new file called today.php. Note that, to save a file with a .php extension in Notepad, you'll need to either select 'All Files' as the file type, or surround the filename with quotes in the Save As dialog; otherwise, Notepad will helpfully save the file as today.php.txt. Type this into the file:

```
```html
<html>
<head>
<title>Today's Date</title>
</head>
<body>
<p>Today's Date (according to this web server) is
<?php
echo( date("l, F dS Y.") );
```
```