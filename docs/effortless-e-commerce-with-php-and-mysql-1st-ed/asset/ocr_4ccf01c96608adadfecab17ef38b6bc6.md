This function will take a piece of data as its lone argument and make it safe to use in database queries. In other words, this function will prevent SQL Injection attacks from succeeding (see Chapter 2, “Security Fundamentals”). The function does three things:

+   - Removes extra slashes if Magic Quotes is enabled
+   - Trims extra spaces from the data
+   - Runs the data through the mysqli_real_escape_string() function

This last task is the most important, because the mysqli_real_escape_string() function will make a value safe to use in a query, keeping in mind the database's configuration and character set in use. The function needs the database connection, which is made available through the global command.

Magic Quotes as a feature has been deprecated and will disappear from future versions of PHP.

# 6. Strip the extra slashes if Magic Quotes is on:

```
if (get_magic_quotes_gpc()) $data = stripslashes($data);
```

Magic Quotes was created to provide a blanket level of security on incoming data, but it's not as secure as using mysqli_real_escape_string(). Hopefully, Magic Quotes is disabled on your server; but if Magic Quotes is enabled, then incoming data will already have slashes applied to potentially problematic characters that might break a query. Those slashes would be a problem, because mysqli_real_escape_string() will also apply slashes, thereby creating two slashes when there should be only one. To prevent that from happening, this line of code checks the Magic Quotes setting and calls the stripslashes() function if Magic Quotes is on.

# 7. Return a trimmed, secure version of the data:

```
return mysqli_real_escape_string (trim ($data), $dbc);
```

The difference between mysqli_real_escape_string() and something like Magic Quotes or addslashes() is that mysqli_real_escape_string() identifies what characters could be problematic based upon the database, the character set in use, and so forth.

The mysqli.inc.php file found in the downloadable source code for this book contains additional code discussed in later chapters.

# 8. Complete the escape_data() function:

```
} // End of the escape_data() function.
```

All included PHP files will omit the closing PHP tag to prevent “headers already sent” errors.

# 9. Save the file.

You may notice that you're not being instructed to include the closing PHP tag here. This is acceptable and, in some situations, actually better. If you were to use the closing tag and then inadvertently leave an extra space or blank line after that tag, the inclusion of this file by other scripts will result