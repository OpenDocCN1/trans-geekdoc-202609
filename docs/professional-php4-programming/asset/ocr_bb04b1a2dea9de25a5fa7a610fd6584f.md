If you see nothing, try using the View Source menu item in your browser. If that shows `<?php phpinfo(); ?>` then Apache is serving up the web page, but it is not correctly configured to hand it off to PHP first. So one of the three `ScriptAlias`/`AddType`/`Action` lines you added to `httpd.conf` must be wrong. Or you forgot to stop and restart Apache. Apache only reads `httpd.conf` once, when it starts. You must restart Apache for changes to `httpd.conf` to take effect.

If you see nothing and the View Source menu item isn't available, check the Apache error logs and review the `httpd.conf` settings. Something is probably configured badly enough to crash Apache.

If all else fails, try commenting out the three lines you've added to `httpd.conf` by inserting a # sign in front of them, and restart Apache. If Apache then works, but PHP doesn't, you at least know it's something in those three lines that is wrong or your installation of PHP itself.

If you cannot find anything wrong with what you typed in `httpd.conf`, test that PHP itself is working properly independent of the browser:

Open up an MS DOS console window and change directory to the C:\php\ or wherever your PHP is installed. Then type:

```
php C:\Program Files\Apache Group\Apache\htdocs\phpinfo.php
```

You may need to substitute a different path if your `phpinfo.php` file is in a different directory.

`php.exe` is invoked, as you are actually handing it your `phpinfo.php` file to work with. PHP should execute the code in that file, and return HTML. If PHP displays the HTML code, then you know `php.exe` is working properly, and that there is something wrong in the way Apache is invoking PHP. Review your `httpd.conf` settings once again.

If `php.exe` works by itself, and Apache works without the three lines to invoke PHP, but they don't work together, your mistake has to be in those three lines.

# Post-Installation

When you install PHP, a file named `php.ini` gets installed with it. Your `phpinfo.php` page should also describe where PHP is looking for your `php.ini` file. Make a backup copy of this `php.ini` file and make sure that `phpinfo.php` is looking in the place where your `php.ini` file exists.

If there simply is no `php.ini` file anywhere, look for a `php.ini-dist` file and copy that over to `php.ini` in the appropriate directory listed in `phpinfo`.

Open `php.ini` file with a text editor, and skim through it to see all the settings. You may want to experiment a little with some of them, and you may want to do some research online at http://php.net/ to see what a particular setting does.

First, if you are not an experienced programmer, it is recommended to increase `error_reporting` one notch to `E_ALL`. Find the Error handling and logging section, and change the line that reads:

```
error_reporting = E_ALL & ~E_NOTICE ;show all errors, except for notices
```