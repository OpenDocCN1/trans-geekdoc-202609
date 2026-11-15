
- Configure your web server so that it expects the PHP interpreter as C:\php\php.exe (FastCGI mode).
- Install PHP 8.2 in C:\php82 and PHP 8.3 in C:\php83.
- Place customized versions of php.ini in each of the two folders created (pay attention to configuration options that have been removed, for example).
- Rename the folder of the PHP version you want to use to C:\php. You may need to stop and restart the web server in the meantime.

With these steps, the "installation" of a PHP version (or the change to it) is reduced to the simple renaming of a folder. This works in exactly the same way under other operating systems.

> Note
> 
> Little known, but very practical: You can also place the php.ini file in any directory under Windows and then set the PHPRC environment variable to the folder in which the php.ini is located. We described this variant in Chapter 2.
> 
> You can also create a separate configuration file for the CLI variant: php-cli.ini. If you also use PHP as a CGI module, you can also specify specific configuration settings in a file called php-cgi.ini.

If you want to use both the CLI version and the CGI version of PHP, you can use a separate, specific INI file for each:

- php-cgi.ini for the CGI variant
- php-cli.ini for the CLI version

### 34.1.2 Other Configuration Files

As already mentioned, php.ini is not the only place for PHP configurations. In conjunction with the Apache web server (see also Chapter 37), there are two further options:

- In an .htaccess file on the web server
- In the Apache configuration file, httpd.conf

There is also a third option that is independent of the web server:

- Within a PHP script

Let's go through these three options in detail:

- In each directory in the Apache web server, you can use .htaccess (depending on the Apache configuration) to issue configuration directives—for example, for access control or authorization (see Chapter 33). If Apache is used as a module, you can also set PHP configuration settings with the following two directives:
  - php_value option value
  - php_flag option value

Use php_value to specify values for configuration options that you would otherwise find in the *php.ini* file. Separate the setting names and values with spaces:

```
php_value session.save_path "/sessiondata"
```

php_flag is the equivalent of a flag—that is, for Boolean values:

```
php_flag short_open_tag On
```

The complete Apache configuration can be found in the *httpd.conf* file; there you can set, for example, which file extensions are handled by which modules and which MIME types they have. It is also possible to set certain PHP settings there. The `php_value` and `php_flag` directives known from *.htaccess* are also available, as well as the following two variants:

- php_admin_value option value
- php_admin_flag option value

The advantage of these two directives is that they cannot be overwritten by *.htaccess*.

Last but not least, you can set configuration values on a script basis. The associated function is called ini_set():

```
<?php
ini_set("include_path", ".:/my/pear/path");
?>
```

So there are many possibilities, but unfortunately not every possibility is always a viable option. This is understandable because it would be fatal, for example, if a script could change the auto_prepend_file option via ini_set(), as auto_prepend_file becomes active before a PHP script is executed. This is why there are four categories for configuration options, which you can find in Table 34.1.

| Category (Constant) | Numerical Value | Options to Change |
|---|---|---|
| PHP_INI_USER | 1 | ini_set() |
| PHP_INI_PERDIR | 2 | .htaccess, httpd.conf, php.ini |
| PHP_INI_SYSTEM | 4 | httpd.conf, php.ini |
| PHP_INI_ALL | 7 | ini_set(), .htaccess, httpd.conf, php.ini |

Table 34.1 The Four Configuration Categories

There are also a few options that can only be set in *php.ini*, such as disable_classes and disable_functions.

You can find a (mostly) up-to-date overview of the categories of the main configuration options in two places:

- On the page in the PHP online manual for the respective module to which the configuration option belongs
- Centrally in the corresponding section of the manual page (http://s-prs.co/v602295; see Figure 34.1)

| Name | Default | Changeable | Changelog |
|---|---|---|---|
| allow_url_fopen | "1" | INI_SYSTEM | |
| allow_url_include | "0" | INI_SYSTEM | Deprecated as of PHP 7.4.0. |
| arg_separator.input | "&" | INI_PERDIR | |
| arg_separator.output | "&" | INI_ALL | |
| assert.active | "1" | INI_ALL | |
| assert.bail | "0" | INI_ALL | |
| assert.callback | null | INI_ALL | |
| assert.exception | "0" | INI_ALL | |

Figure 34.1 Overview of the Configuration Options, in Alphabetical Order

## 34.2 Configure What?

This section contains a commented excerpt from the actual php.ini file that is supplied with PHP. Of course, there is not enough space to go into every option explicitly, but the most important sections should nevertheless be briefly presented here. We will focus on the general PHP options; a list of the most important configuration switches for the PHP extensions can be found in the reference sections of the respective chapters.

> **Note**
> 
> We use the `php.ini-production` file directly from the PHP version management system at http://s-prs.co/v602252 (as of December 2024; see Figure 34.2). We have changed, modified, or completely omitted some settings.

![](img/ae7820c36e8f24c1623d26668b28e80e_919_0.png)

Figure 34.2 The Latest File Versions Are Always Available on GitHub

The first major section is called Language Options and contains general settings relating to the PHP installation—for example, the compatibility mode for Zend Engine 1 or the use of the short PHP tag (`<?`):

```
;;;;;;;;;;;;;;;;;;;;;
; Language Options ;
;;;;;;;;;;;;;;;;;;;;;
; Activate PHP for Apache
engine = On

; activate <?php
short_open_tag = Off

; Precision of decimal numbers (decimal places)
precision = 14
```

The output of the resulting PHP code can be both buffered and automatically compressed:

```
; Enable buffer (buffer size in bytes)
output_buffering = 4096
; Pass total output to buffer function
;output_handler = 
; Compress output automatically via zlib
zlib.output_compression = Off
;zlib.output_compression_level = -1
; Special buffer function when using
;  zlib.output_compression ;
zlib.output_handler = 
; Empty the output buffer after each call to echo or print ;
(corresponds to a call to flush())
implicit_flush = Off
; Function to be called if an unknown class is found during
; deserialization
unserialize_callback_func=
; maximum nesting depth during deserialization
;unserialize_max_depth = 4096
; Precision in decimal places during serialization; -1 = best possible
serialize_precision = -1
```

Despite the now abolished (and never sufficient anyway) safe mode, there are certain protection mechanisms for PHP installations:

```
; Directory in which file operations are allowed (incl. subfolders)
;open_basedir = 
; List of disallowed functions (phpinfo, system ... makes sense)
disable_functions = 
; Classes that may not be used (separated by commas)
disable_classes = 
; Colors for .phps (syntax highlighting)
;highlight.string = #DD0000
;highlight.comment = #FF9900
;highlight.keyword = #007700
;highlight.default = #0000BB
;highlight.html = #000000
; Enable garbage collector
zend.enable_gc = On
; Maximum length for exceptions
zend.exception_string_param_max_len = 0
```

The Resource Limits section contains some restrictions on the resources PHP is allowed to use, including timeout and memory limits:

```
;;;;;;;;;;;;;;;;;;;;;;;;
; Resource Limits ;
;;;;;;;;;;;;;;;;;;;;;;;;
max_execution_time = 30 ; Maximum script runtime
max_input_time = 60 ; Maximum time for parsing the input
max_input_nesting_level = 64 ; Maximum nesting depth
; in the input ;
max_input_vars = 1000 ; Maximum number of input variables
;max.multipart.body_parts = 1500 ; Maximum parts for multipart requests
memory_limit = 128M ; Maximum memory consumption
```

When errors occur, there are several ways to react. Among other things, PHP offers logging of errors (with Apache) and the option of not sending an error message to the web browser. The latter is unfavorable during development and testing but is extremely useful on the production server:

```
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Error handling and logging ;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Levels for error_reporting:
; E_ALL - All errors and warnings
; E_ERROR - (Fatal) runtime errors
; E_RECOVERABLE_ERROR - Almost fatal runtime errors
; E_WARNING - Non-fatal runtime errors
; E_PARSE - Parser errors
; E_NOTICE - Run-time notices
; E_CORE_ERROR - errors when starting PHP;
; E_CORE_WARNING - warnings when starting PHP;
; E_COMPILE_ERROR - errors when compiling;
; E_COMPILE_WARNING - warnings when compiling
; E_USER_ERROR - user-specific error messages
; E_USER_WARNING - user-specific warnings
;
; E_USER_NOTICE - User-specific notices;
; E_DEPRECATED - Warnings for code that will no longer work in future PHP versions;
; E_USER_DEPRECATED - User-specific warnings for obsolete code
;
; Examples:
;
; - Everything except warnings and compatibility notes
;
; error_reporting = E_ALL & ~E_NOTICE & ~E_STRICT & ~E_DEPRECATED
;
```
