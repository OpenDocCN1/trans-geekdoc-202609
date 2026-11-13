PHP should look for files that you ask it to include. Set it so it contains "." (the current directory).

Depending on whether your server is running under Windows or UNIX, you may need to surround your setting with quotes:

Under UNIX:
include_path=..:/another/directory

Under Windows:
include_path=".;c:\\another\\directory"

# Increasing Security with Includes

PHP scripts will sometimes contain sensitive information like usernames, passwords, and other things you don't want the world to have access to. By now you're probably used to the mysql_connect function, which requires you to put your MySQL username and password in a PHP script that needs access to a database. While you can simply set up MySQL so that the username and password used by PHP cannot be used by potential hackers (by setting the `Host` field in the `user` table as described in Chapter 8), you would probably still rest easier knowing that your username and password are protected by an extra level of security.

"But wait a minute," you might say. "Since the PHP is processed by the server, nobody gets to see my password anyway, right?" Right, but consider what would happen if PHP stopped working on your server. Whether due to an accidental software misconfiguration made by a well-meaning associate, or because of some other factor, if PHP stopped working on your server, the PHP pages would be served up as plain text files, with all your PHP code (including your password) there for the world to see!

To guard against this kind of security breach, you should put any security-sensitive code into an include file, and place that file into a directory that's not part of your Web server's directory structure. If you add that directory to your PHP `include_path` setting (in `php.ini`), you can refer to the files directly with the PHP `include` function, but have them tucked away safely somewhere where your Web server can't display them as Web pages.

For example, if your Web server expects all Web pages to exist in `/home/httpd/` and its subdirectories, you could create a directory called `/home/phpinc/` to house all of your include files. Add that directory to your `include_path`, and you're done! The next example shows how you can put your database connection code into an include file:

```
<!-- dbConnect.inc (in /home/phpinc/) -->
<?php
```