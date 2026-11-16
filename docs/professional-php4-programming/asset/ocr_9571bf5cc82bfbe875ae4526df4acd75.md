If you get a 500 Internal Server Error you probably have a typo in `httpd.conf`. Check the Apache `error_log` for a message.

If you see nothing in the browser, use the View Source menu to see what might be there. If you see `<?php phpinfo(); ?>` in the browser, then Apache is not correctly configured in `httpd.conf` to know that PHP handles documents of mime-type `applications/x-httpd-php` and that files that end in `.php` are of that mime-type. Thus, you are seeing the file as if it were a regular text (or HTML) file. Review the `httpd.conf` settings that involve PHP.

# # Post-Installation

While you are compiling, you might as well compile PHP as a standalone binary (also known as CGI). Even though we are installing PHP as a module, and not a CGI, the standalone binary is incredibly useful. With it, you can execute PHP scripts from the command line, and thus you can use cron to schedule PHP scripts to be executed at specific times/dates.

There are some security issues involved with using PHP as a CGI. Including the PHP binary we are about to create **inside** the `DocumentRoot` directory, or in the `cgi-bin` directory is a security hazard. You already have PHP as a module, and have no need for PHP as a CGI.

> You might want to have PHP installed, both as a module and as a CGI, in the same web server. In that case, read the security chapter of the online PHP manual carefully (`http://www.php.net/manual/en/security.php`). If you don't completely understand that, do not put a PHP CGI binary in your web directory. It would cause a fairly big security hole.

To compile PHP as a standalone binary, change into the PHP source directory, and copy the `config.sh` script to `config.cgi.sh`:

```
cd /usr/local/src/php-4.x.xx.xx
cp config.sh config.cgi.sh
```

Edit the new `config.cgi.sh` file and delete the line that has `--with-apxs=` in it.

We won't be putting the resulting binary in the `DocumentRoot`. For security reasons, you should add the following two lines in case you do that when you've been told not to:

```
--enable-discard-path \
--enable-force-cgi-redirect \
```

Be sure that all the lines **except** the last line have `\` at the end.

> Never copy the `php` binary into the web tree or `cgi-bin` directories.

Save and quit, and then do:

```
./config.cgi.sh
make
```