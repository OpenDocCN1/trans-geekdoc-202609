Next, we use `fgets` to fetch a “chunk” of the file, beginning at the current location and running to the next line feed character. We get the string back, and `fgets` moves the internal PHP file pointer for the file handle forward accordingly.

There are many more functions for reading a file using a file handle. One is `fgetss` (note the double ’s’), which is almost exactly the same as `fgets` but strips out any HTML tags it finds, in the same way the `strip_tags` function would. Another is `fscanf`, which formats the output from the file in the same way `printf` does. It’s well worth browsing the file system functions[3] for “goodies” in an idle moment.

PHP provides fairly simple functions for handling files, but better yet is to use PEAR::File. This provides an even simpler API for reading files and allows you to take advantage of other PEAR classes for performing tasks like finding a file in a file system and modifying an .htaccess file. PEAR::File can be found at the PEAR Website[4]; the version used here was 1.0.3 (see Appendix D for instructions on how to install PEAR modules).

One particularly useful feature of PEAR::File is that it allows files to be locked while they’re being read, which means you won’t suffer conflicts where two people work on the same file at the same time. PEAR::File also deals with errors nicely.

![](bbox=[0.106, 0.503, 0.177, 0.546])

# # Leave Databases to the Experts

Although it’s possible to store data in files in more or less the same way as you would in a database (especially when you consider the locking mechanisms PHP makes available), it’s generally a good idea to leave this sort of work to MySQL. Writing your own database in PHP is a very complex problem so there’s no point “reinventing the wheel” unless you really have to.

Let’s see how we might read the entire contents of a file using PEAR::File:

```
```php
<?php
// Include PEAR::File
require_once 'File.php';

// Read the entire file and display, using a shared read lock
echo File::readAll('demo/writeSecureScripts.html',
```
```

[3] http://www.php.net/filesystem
[4] http://pear.php.net/package-info.php?pacid=43