# Core PHP Programming

The functions that use the stat cache are: stat, file_exists, filemtime, filetime, inode, filegroup, fileowner, fileperms, filesize, filetype.

```
//make sure info isn't cached
clearstatcache();

// get size of this file
print(filesize(_FILE_));
```

# define_syslog_variables

The define_syslog_variables function emulates the configuration directive of the same name. It causes the constants for use to be created as variables. The functions that interact with the system log are closelog, openlog, and syslog.

```
define_syslog_variables();
```

# boolean dl(string extension)

Use the dl function to load a dynamic extension module. The function returns FALSE if the module could not be loaded. The path to these modules is set in php.ini, so you need type only the name of the module file.

```
//load windows mysql module
l("php_mysql.dll");

//show diagnostics
phpinfo();
```

# integer error_reporting(integer level)

The error_reporting function sets the level of error reporting and returns the previous value. The level argument is a bitfield, so you use the bitwise OR operator (| to put together the type of reporting you would like. By default PHP uses a level of seven, which is Errors, Warnings, and Parser Errors. Refer to Table 11.7, which lists error levels.