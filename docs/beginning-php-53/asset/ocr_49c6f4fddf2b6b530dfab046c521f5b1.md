Now press Enter. If all has gone according to plan, you should see something like Figure 2-10.

![](bbox=[0.21, 0.13, 0.71, 0.28])

Figure 2-10

If your Apache server is not running on the standard HTTP port (80) — for example, if you installed MAMP and used its default port of 8888 — modify your URL appropriately; for example: http://localhost:8888/testing.html .

This means that Apache is up and running, and you’ve successfully located the Web server’s document root. If you don’t get this page, it’s likely that one of two things is happening:

+   - [ ] If you get a 404 Not Found error, this means that the testing.html file is not in the Web server’s document root. Double-check the location of the document root folder — take a look at the documentation if necessary — and make sure your testing.html file is inside the folder.
+   - [ ] If you get a Connection Refused error, the Apache Web server is not running (or it’s running on a different port). Check that you’ve started the Web server, and that it’s configured correctly (again, the documentation that came with the package should help here).

# Testing PHP

Now that you know Apache is working correctly, it’s time to make sure PHP is installed and working. This is where you get to write your very first PHP script!

Open your text editor again, and create a new file with the following contents:

```
<?php
phpinfo();
?>
```

Save this file as testing.php in the same folder as your testing.html file — that is to say, the document root folder. Now type the following into your Web browser’s address bar (adjusting the HTTP port number if necessary):

http://localhost/testing.php

Press Enter, and you should see a page similar to Figure 2-11 appear. (If you’ve installed PHP 5.3 you will, of course, see references to version 5.3 in your page, rather than version 5.2.) This is the result of running the phpinfo() function, a built-in PHP function that displays information about the version of PHP that’s installed. This means that you have successfully installed both Apache and PHP. Congratulations!