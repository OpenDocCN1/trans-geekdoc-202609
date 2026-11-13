> > PHP looks for the socket to MySQL in /tmp/mysql.sock. If you have more than one MySQL installation and need PHP to connect to the socket in another location, you need to specify that in the mysql_connect() function, like this:
> >
> > ```
> > mysql_connect("localhost:/path/to/mysql.sock",
> > "username", "password");
> > ```

In Mac OS X you probably want to use the version of Apache that ships with the OS. Therefore, you probably won't need to do any configuring or compiling of Apache. Simply start by configuring PHP the way you want it, using all the libraries and flags you need. Simply add the --with-apxs flag when compiling PHP, and PHP makes itself part of your Apache configuration.

Depending on the state of PHP 5 and OS X at the time you're installing, PHP may require some extra libraries, like libxml2. You should be able to get what you need from either Darwin Ports at http://www.opendarwin.org/projects/darwinports/ or Fink at http://fink.sourceforge.net/.

You still need to make the changes listed earlier in this section to your httpd.conf file. In OS X, that file can be found in /etc/httpd.

# # PHP Configuration

The php.ini file is extremely large and has more options than we can cover here. A full list of options and potential settings can be found at http://www.php.net/manual/configuration.php. Here are a few highlights.

# ## Globals

We've talked a lot in this book about the use of global variables. If possible you should have the register_globals line set to Off. This configuration requires you to use the $_GET, $_POST, $_SERVER, and other like-named arrays when using global variables, which keeps your applications more secure. But if you're working off legacy applications, it may be tough to make all the changes needed to have register_globals set to Off. If you are able to set register_globals to Off, you can prevent anyone from setting an internal PHP variable by referring to that variable in the URL or in a POST.

# ## MySQL configuration entries

The following are some of the MySQL configuration entries:

+   - mysql.allow_persistent
+   - mysql.max_persistent