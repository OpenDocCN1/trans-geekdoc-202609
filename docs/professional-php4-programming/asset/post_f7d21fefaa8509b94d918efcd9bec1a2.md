
Make a backup copy of this file, and use your favorite editor to review the settings. If you don't like the default DocumentRoot where all your web pages will go, which is /usr/local/apache/htdocs/ you can alter the setting in <Directory ...>. You'll also be editing this httpd.conf later to integrate PHP with Apache.

You can skim through the file to see what other options Apache has available for you. It's handy to have some kind of idea what's in there if you run into trouble later or want to implement a new feature on your web server that requires altering Apache configuration.

If you have Apache working properly, you probably want Apache to be always running and automatically start on boot. You can add a script in /etc/rc.d/init.d/ and name it apache with the following line in it:

```
/usr/local/apache/bin/apachectl start
chmod 755 /etc/rc.d/init.d/apache
```

You'll need to change the path if you have deviated from the above instructions. Then, in /etc/rc.d/rc3.d/ you can do:

```
ln -s ../init.d/apache S99apache
```

The first two commands create an executable shell script that is available for any of the 6 different boot levels. Usually your computer boots into level 3, but in case of an emergency, you can boot into level 1 where fewer applications are started. The last command creates a soft link in the rc3.d directory. Commands in that directory that begin with "S" are executed at boot time in alphabetical order. Since you want Apache to start rather late in the process, we started it with S99 rather than a lower number.

If you are not running Linux, or even if you are running a different distribution of Linux, the directory structure for the rc.d, init.d, and rcX.d directories (where X is 1 through 6) might be different, but most Linux distributions have a similar setup.

## What Can Go Wrong?

If configure or make fails, search the Apache web site for your operating system. There may be some information to help you install Apache.

If configure, make, and make install seemed to go OK, but Apache doesn't start, check the error_log file which is in /usr/local/apache/logs/error_log by default.

If Apache works fine when you start it by hand but not during reboot, do this right after a reboot:

```
tail /var/log/messages
```

The tail command shows you the last 10 lines from the file supplied. /var/log/messages is a log of operating system messages. It should have some messages about Apache's attempt to start up. If you see absolutely nothing about Apache, you may need to view more lines using:

```
tail -n 20 /var/log/messages
```

This will show the last 20 lines rather than the default 10. You can also add | grep apache to the end of the command to search for apache in the output.

If nothing at all appears, check the filename and link in /etc/rc.d that you created.

## Installing PHP

You're finally ready to actually configure, compile, and install PHP now. First download the latest stable source release from http://php.net/ into your /usr/local/src directory. Untar/gunzip the files:

```
tar -xzf php-4.x.x.tar.gz
```

Change into the PHP directory:

```
cd php-4.x.x
```

You could jump right in and do ./configure. However, if you added anything other than MySQL and Apache to your computer, and want to integrate PHP with it, you may find yourself re-configuring the other third party software. In the meantime, the configure command that you used to install PHP will have scrolled off the screen. Rather than try to dig back through your history list to find it, we're going to create a shell script to configure PHP. Create a file named config.sh and put the following lines in it:

```
./configure \
--with-apxs=/usr/local/apache/bin/apxs \
--with-mysql=/usr/local/mysql
```

If you have any other PHP extensions you want to add, put them in on separate lines with \ at the end. Make sure the last line does not end with a \.

Note that --with-apxs is used instead of --with-apache. This allows you to install PHP as a dynamic shared object (DSO) instead of a static module. This means you'll be able to upgrade PHP, without having to re-compile Apache just because you want to upgrade PHP. If you use --with-apache, you'll need to re-compile Apache when it's time to upgrade PHP. If you are using a web server other than Apache, you'll need to substitute something appropriate for --with-apxs.

Save the file and do:

```
chmod 755 config.sh
```

You can now do:

```
./config.sh
```

This attempts to configure PHP.

If you are following these instructions without deviations, everything should work just fine. If you deviated a little to add more features, the script will let you easily configure with and without them by editing the config.sh file and deleting or adding lines.

Pay attention as configure prints out various status messages: some of the configure flags (like --with-mysql) might fail, but the configure itself will continue successfully.

At the end, you should see a message in an ASCII art box:

```
+---------------------------------------------------------------------------+
| License:|
| This software is subject to the PHP License, available in this|
| distribution in the file LICENSE By continuing this installation|
| process, you are bound by the terms of this license agreement.|
| If you do not agree with the terms of this license, you must abort|
| the installation process at this point.|
+---------------------------------------------------------------------------+
```

## What Can Go Wrong?

Sometimes you might see error messages such as these:

*** WARNING ***
Your /usr/local/apache/bin/apxs script is most likely broken.

*** WARNING ***
You will be compiling the CGI version of PHP without any redirection checking...

*** WARNING ***
You chose to compile PHP with the builtin MySQL support.

If you see any of these, then don't go ahead with make and make install, as they will not work.

The first one actually gives you a link to the PHP FAQ. It's unlikely that you'll see this one, unless you managed to install an old version of Apache, or used the path to the old version of the apxs script instead of the one you installed above.

The second one about compiling the CGI version of PHP without redirection checking means that you misspelled (or forgot) the --with-apxs line in your config.sh file above, or that you provided an invalid path to the apxs script.

The last of them indicates that PHP did not find the MySQL you installed, but is going to use a built in MySQL interface. The odds on this interface being the correct version to match up with your MySQL installation are quite slim. More importantly, if Apache is using MySQL in other modules such as mod_auth_mysql, continuing blindly and using the resulting PHP module to Apache will simply crash Apache. Go back and check your --with-mysql line in config.sh for spelling and the correct path to your MySQL installation.

If you are trying to use other PHP extensions and having trouble with configure, review the config.log file for any error messages that seem related to the problem. Also double-check your spelling in config.sh as well as any directories. You can do:

```
configure --help | less
```

Use the space bar and arrow keys to get a very brief overview of the options to configure. It's very easy to misspell one of the directives or a path or forget to use a path. Also note that some directives require other directives to be useful. --with-gd, for example, is rather pointless without at least one of --with-jpeg-dir, --with-png-dir, or --with-tiff-dir since GD itself relies on the underlying graphics technologies to do its job.

If you attempt to do config.sh again, do rm config.cache and make clean first:

```
rm config.cache
make clean
./config.sh
```

If you don't do this, configure is likely to remember the old, broken settings and simply repeat the same mistake as before, ignoring the new directives you have provided.

Similarly, if you don't do make clean, the compiler might not realize that you've altered the configure settings, and think that the files it has already compiled can be safely skipped. This actually is usually correct, since the files that were successfully compiled are usually fine, but since there are rare occurrences where it matters, it's safer to do make clean anyway. It will take longer to compile, but you'll know you're getting what you asked for this time with the new configure options.

```
make distclean
```

This should completely reset everything to exactly the way it was after you untarred/gunzipped PHP; the way it was before you did configure, make, or make install.

## Compiling PHP

After you've successfully done config.sh, you can do:

```
make
```

If that works without error, do:

```
make install
```

If configure seemed to work, but make failed, then you need to review config.sh and try again. The output from make seems rather obscure, but you can usually tell which extension was being compiled at the time that it failed. You can do make again and it will probably quickly repeat the error message. It doesn't need to re-compile all the files it compiled already, and will rush through them and get right to the one that didn't work. But be sure to do make clean (see above) when you're ready to try again with different settings.

## What Can Go Wrong?

If things are going wrong at this point, and are not already covered in this book, then copy the error message, and go to http://php.net/support.php. Then click on the link to the PHP-General mailing list archive and paste in your error message to the search engine. Also read the FAQ at http://php.net/FAQ.php.
