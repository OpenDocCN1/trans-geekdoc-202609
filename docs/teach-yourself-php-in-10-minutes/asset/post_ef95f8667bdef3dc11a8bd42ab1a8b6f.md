
## Logging Errors

You can accomplish most simple error logging requirements by using the `error_log` function. You can use this function to write an error message to the web server log file or some other local file, send it via email, or transmit it to a remote debugging service.

The `error_log` function takes the following arguments:

```
error_log($message, $message_type, $destination, $extra_headers);
```

Only the `message` argument is required, and the default action is to write this message text to the usual PHP log file. In most cases, this is your web server's log file.

The `message_type` argument specifies a number that determines what type of destination is supplied. Its possible values are shown in Table 22.2.

### Table 22.2. message_type Argument Values in error_log

| Value | Description |
| :--- | :--- |
| 0 | The message will be written to the default web server log file. |
| 1 | The message will be sent via email; `destination` contains the address to send to, and `extra_headers` contains optional email headers. |
| 2 | The message will be sent to a remote debugging service; `destination` contains the remote hostname. Note that remote debugging is not available in PHP 4 and later. |
| 3 | The message will be appended to a local file; `destination` contains the filename and path. |

For example, to send an error message via email, you might use the following statement:

```
error_log("An error occurred in your script", 1, "chris@lightwood.net", "From: PHP Script Error <errors@yoursite.com>");
```

## Suppressing Errors and Warnings

PHP allows you to suppress warning messages in your script. You can either turn off warnings completely or select individual commands for which any errors will not be displayed.

## The Error Suppression Operator

If you want to stop a warning message from appearing for a particular statement only, you can use the @ symbol to silence it. You might want to do this so that your custom error messages are displayed.

For example, when you connect to a MySQL database, PHP raises its own error if the connection fails. You can also detect the failure by checking whether a valid database resource handle was returned. The following code uses the @ symbol to suppress the PHP error message so that only your message is displayed onscreen:

```
$db = @ mysql_connect("localhost", "username", "password");
if (!$db) {
    echo "Database connection failed";
    exit;
}
```

You can place the @ symbol before any expression in PHP. It causes any error messages generated as a result of that expression being evaluated to be ignored.

In the preceding example, the expression being silenced is the database connection attempt. As a general rule, if something in PHP has a value, it can be prefixed with the @ symbol. You cannot prepend an @ symbol to a language construct such as a function definition or conditional statement.

**Parsing Errors** The @ operator does not hide error messages caused by parsing errors in script.

The following statement is also valid, although it does not make it clear that you are expecting the error message to originate with `mysql_connect`:

```
@ $db = mysql_connect("localhost", "username", "password");
```

**Error Suppression** If you have used `set_error_handler` to specify a custom error handler in your script, the @ operator will have no effect.

## Preventing Error Display

The configuration directive `display_errors` can be set to `Off` in `php.ini` to prevent any errors from being displayed onscreen. You will learn how to change the value of `php.ini` settings in Lesson 23.

If you choose to prevent error display for your whole website this way, you should turn on the `log_errors` setting so that errors and warnings are written to a file; otherwise, you will have no way of knowing about potential problems. You should not consider turning `display_errors` off while a website is in development.

## Summary

In this lesson you have learned how to detect and handle errors in PHP scripts. In the next lesson you will learn about the various PHP settings that you can configure to suit your particular needs.

## Lesson 23. PHP Configuration

In this lesson you will learn how to configure global PHP settings at runtime, using the php.ini file, and per-directory settings, using .htaccess.

## Configuration Settings

PHP allows you to tune many aspects of its behavior by using a set of configuration directives. These directives can be global for your entire web server, or you can make local changes that apply only to certain scripts.

## Using php.ini

PHP's configuration file is named `php.ini`. Its location is set at compile time; by default, it is located in `/usr/local/lib/php.ini` on Linux/Unix servers and `C:\WINDOWS\php.ini` on Windows systems.

The `php.ini` file contains a list of configuration directives and their values, separated by equals signs. The default `php.ini` file distributed with PHP is well documented, with plenty of comments. Any line that begins with a semicolon is considered a comment, and sections of the file are broken up using headings in square brackets, which the compiler also ignores.

Listing 23.1 shows an extract from an unchanged `php.ini` file for PHP 5 that contains the log settings. As you can see, for many setting changes, you do not even need to refer to the online documentation.

### Listing 23.1. An Extract from php.ini

```
; Print out errors (as a part of the output). For
; production web sites,
; you're strongly encouraged to turn this feature off,
; and use error logging
; instead (see below). Keeping display_errors enabled
; on a production web site
; may reveal security information to end users, such as
; file paths on your Web
; server, your database schema or other information.
display_errors = On

; Even when display_errors is on, errors that occur
; during PHP's startup
; sequence are not displayed. It's strongly recommended
; to keep
; display_startup_errors off, except for when debugging.
display_startup_errors = Off

; Log errors into a log file (server-specific log, stderr,
; or error_log (below))
; As stated above, you're strongly advised to use error
; logging in place of
; error displaying on production web sites.
log_errors = Off

; Set maximum length of log_errors. In error_log information
; about the source is
; added. The default is 1024 and 0 allows to not apply any
; maximum length at all
log_errors_max_len = 1024
```

> **True or False** Boolean values in `php.ini` can be set to `true` (that is, `on` or `yes`) or `false` (that is, `off`, `no`, or `none`). These values are not case-sensitive.

When it runs as a web server module, `php.ini` is read when the web server process starts, and changes made to the configuration file do not take place until the web server is restarted.

If your web server runs PHP as a CGI binary, the `php.ini` settings are loaded each time a script is run because a new `php` process is started. Similarly, command-line PHP loads the settings from `php.ini` each time a script is run.

## Alternate php.ini Files

You can create separate `php.ini` files to apply for the different ways PHP can be run. If you create a file named `php-SAPI.ini` (replacing `SAPI` with a valid SAPI name), that file is read instead of the global `php.ini`.

For instance, to provide a different set of directives only for command-line PHP, you would use a configuration file named `php-cli.ini`. For the Apache web server module, the filename would be `php-apache.ini`.

On a Windows system, a `php.ini` file in the Apache installation directory is used before one in `C:\WINDOWS`. This allows you to maintain different PHP settings for multiple web servers on the same machine.

To force the use of a particular configuration file, you must invoke `php` with the `c` option. In a shell script, you might change the first line to the following to force a custom configuration file to be used only for that script:

```
#!/usr/local/bin/php c /path/to/php.ini
```

## Per-Directory Configuration

Apache web server allows you to use a per-directory configuration file named `.htaccess` to supply custom web server directives. PHP supports the use of `.htaccess` to override the global settings from `php.ini`.
