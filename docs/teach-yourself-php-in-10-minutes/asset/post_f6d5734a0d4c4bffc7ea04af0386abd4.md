

```
display_errors = On
log_errors = Off
```

You can use the error_log directive to specify an alternate filename, as in the following example:

```
error_log = /tmp/php_log
```

## Configuring PHP Extensions

Some PHP extensions have their own directives that can be configured in php.ini to adjust the behavior of that extension.

For clarity in the configuration file, section headings are used to separate extension-specific settings. For instance, all the settings that affect the MySQL extension are found in a section of php.ini that begins [MySQL]. Each directive name also has a prefix that indicates the extension to which it belongs (for example, mysql.connect_timeout or session.cookie_path).

You can find documentation for extension-specific configuration directives in the online manual pages for each extension.

## Configuring System Security

Some of the directives in php.ini that are not covered in this lesson, most notably the safe_mode directive and its related settings concern server security. These configuration options allow you to restrict certain types of functionality on the web server, and you will learn about them in Lesson 24, "PHP Security."

## Loadable Modules

PHP allows you to load certain extensions at runtime. This means that you can extend the functionality of PHP without needing to recompile from source.

### Loading Extensions on Demand

You use the dl function to dynamically load an extension module. You build extensions as dynamically loadable objects when PHP is compiled, by using the --with-EXTENSION=shared switch. For instance, running the following configure statement causes PHP to be compiled with MySQL support linked in but with socket support as a loadable extension:

```
./configure --with-mysql --with-sockets=shared
```

The argument given to dl is the filename of the extension. In the case of the sockets extension, it would be called sockets.so on Linux/Unix but php_sockets.dll on Windows systems.

**Loadable Extensions** Whether the dl function is available is governed by the enable_dl directive in php.ini. You may find that on a shared web hosting service, this feature is not available to you.

To check whether an extension is loaded into PHP, you use the extension_loaded function. Given an extension name argument, this function returns true or false, depending on the presence of that extension. Note that PHP cannot tell whether an extension was loaded by using dl or is compiled in.

### Loading Modules on Startup

If you have extensions as loadable modules and want them to be loaded into PHP without needing to run dl in every script, you can use the extension directive in php.ini to provide a list of extensions to load at startup.

Each extension is given on a separate line, and there is no limit to the number of extensions you can load in this way. The following lines from php.ini ensure that the sockets and imap extensions are loaded automatically on a Linux/Unix server:

```
extension=imap.so
extension=sockets.so
```

On a Windows web server, the configuration lines need to look like this, to reflect the difference in filenames between the two platforms:

```
extension=php_imap.dll
extension=php_sockets.dll
```

## Summary

In this lesson you have learned how to configure PHP at runtime. In the next lesson you will learn about PHP's Safe Mode and how to minimize security threats to your website.

## Lesson 24. PHP Security

PHP is undoubtedly a very powerful server-side scripting language, but with great power comes great responsibility. In this lesson you will learn how to use PHP's Safe Mode to make sure that some of the potentially dangerous features of PHP are locked down.

## Safe Mode

PHP's Safe Mode attempts to provide a degree of basic security in a shared environment, where multiple user accounts exist on a PHP-enabled web server.

When a web server is running PHP in Safe Mode, some functions are disabled completely, and others are available with limited functionality.

### Restrictions Enforced by Safe Mode

Functions that attempt to access the filesystem have restricted functionality in Safe Mode. The web server process runs under the same user ID for all web space accounts and must have the appropriate read or write permission to access a file. This is a requirement of the underlying operating system and has nothing to do with PHP itself.

When Safe Mode is enabled and an attempt is made to read or write a local file, PHP checks whether file ownership of the script is the same as that of the target file. If the owner differs, the operation is prohibited.

**Write Permission** Although Safe Mode implements measures to prevent you from opening another user's files through PHP, the operating system's file permissions may still allow read or even write access to those files at a lower level. Be aware that a user who has shell access to the web server will be able to read any files that are accessible by the web server and write to any file that has global write permission.

The following core filesystem functions are restricted by this rule:

- chdir
- chgrp
- chown
- copy
- fopen
- highlight_file
- include
- link
- mkdir
- move_uploaded_file
- parse_ini_file
- rmdir
- rename
- require
- show_source
- symlink
- touch
- unlink

Functions that are part of PHP extensions that also access the filesystem are similarly affected.

**Loadable Modules** The `dl` function is disabled in Safe Mode, regardless of the owner of the extension file. Extensions must be loaded into PHP at startup, using the `extension` directive in `php.ini`.

Functions that execute host programs are disabled unless they are run from the directory given in the `safe_mode_exec_dir` directive, which you will learn about in the next section. Even if execution is allowed, arguments to the commands are automatically passed to the `escapeshellcmd` function.

The following program execution functions are affected by this rule:

- exec
- shell_exec
- passthru
- system
- popen

In addition, the backtick operator (`) is disabled.

The `putenv` function has no effect when run in Safe Mode, although no error is produced. Similarly, other functions that attempt to change the PHP environment, such as `set_time_limit` and `set_include_path`, are ignored.

## Enabling Safe Mode

You turn Safe Mode on or off by using the `safe_mode` directive in `php.ini`. To activate Safe Mode for all users on a shared web server, you use the following directive:

```
safe_mode = On
```

As you learned in the previous section, functions that access the filesystem perform a check on the owner of the file. By default, the check is performed on the file owner's user ID, but you can relax this to check the owner's group ID (GID) instead by turning on the `safe_mode_gid` directive.

If you have shared library files on your system, you can use the `safe_mode_include_dir` directive to get a list of locations for which the UID/GID check will not be performed when an `include` or `require` statement is encountered.

**Include Directories** If you want to list more than one location in the `safe_mode_include_dir` directive, you can separate them using colons on Linux/Unix or semicolons on Windows systems just as you do with the `include_path` setting.

To allow inclusion of files in `/usr/local/include/php` for any user in Safe Mode, you would use the following directive:

```
safe_mode_include_dir = /usr/local/include/php
```

To provide a location from which the system can be executed, you use the `safe_mode_exec_dir` directive.

To allow programs in `/usr/local/php-bin` to be executed in Safe Mode, you would use the following directive:

```
safe_mode_exec_dir = /usr/local/php-bin
```

**Executables** Rather than allow execution of all programs from `/usr/bin` or some other system location, you should create a new directory and copy or link only selected binaries into it.

To allow setting of certain environment variables, you use the `safe_mode_allowed_env_vars` directive. The value given is a prefix, and by default it allows only environment variables that begin with `PHP_` to be changed. If more than one value is given, the list should be separated by commas.

The following directive also allows the time zone environment variable, `TZ`, to be changed:

```
safe_mode_allowed_env_vars = PHP_, TZ
```

