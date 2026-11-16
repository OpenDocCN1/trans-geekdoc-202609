Accessing protected documents can be done by requesting for the URL http://www.mydomain.com/cgi-bin/php/some/protected/file.html. This request would bypass the web server's security mechanisms, and output the contents of http://mydomains.com/some/protected/file.html. This happens because PHP never requests this file from the web server, but fopen it directly from the file system.

PHP has various options to stop this happening. If we compile PHP with the `-enable-force-cgi-redirect` option, then PHP will not allow requests directly to the parser itself. We can also use the `doc_root` and `user_dir` configuration directives to limit PHP's access.

> The `-enable-force-cgi-redirect` configuration option has only been tested with Apache and is not guaranteed to work with any other server. It relies on Apache setting the non-standard CGI variable `REDIRECT_STATUS`. If you are using a server other than Apache, talk to your vendor to see if this option will work.

Another option of making this setup more secure is to place the PHP parser outside of the web root. A good location might be `/usr/local/bin/php`. This does have one disadvantage that you need to place the line:

```
#! /path/to/php
```

at the top of the file so that the web server knows where to find the PHP parser. We would also need to make our scripts executable. To get PHP to handle the `PATH_INFO` and `PATH_TRANSLATED` variables correctly use the compile time configuration option `-enable-discard-path` during setup.

# Configuring PHP

PHP has various options in the `php.ini` file that can make it more secure by limiting what it can access. The ones you are most likely to use for this purpose are discussed below.

# display_errors

This option should be set to `false`. Also, implement error handlers on production machines. This is because PHP reveals the path information for the script and maybe a variable name when an error occurs. This can give an attacker some more information about the system. So set this to `false` in production environments. By default, this option is set to `true` in the `php.ini` file. If you have set this to `false` you might want to set up the `error_log` configuration option which should point to the file where you want PHP to log any errors it encounters.

# error_reporting

PHP provides various debugging and error handling capabilities. These need to be understood and used carefully to prevent them from compromising the security of the system. Depending on the kinds of errors and warnings to report we can use the `error_reporting()` function to set this value, or set a value for `error_reporting` in the `php.ini` file. PHP defines various constants to help us do this. They are listed here with the different types of error they enable: