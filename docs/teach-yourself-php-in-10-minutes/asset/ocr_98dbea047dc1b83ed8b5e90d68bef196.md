Often you need to ensure that include files are kept in a directory that is not directly accessible by a web server. The following example defines an include path that contains a directory parallel to the web root of /home/chris/public_html :

```
php_value include_path ../home/chris/include
```

The period character ( . ) is used to indicate the current working directory, and in this example, it is given higher priority than the defined include directory. In this case, if an include statement finds a matching file in both locations, the one in the working directory will be used. This type of configuration allows you to use shared library files across your server but override them for some scripts when necessary.

The auto_prepend_file and auto_append_file directives allow you to specify files that are automatically added at the start and end of each PHP script. The filename given is found in include_path , or a full path to the file can be given.

A common use for auto_prepend_file is to automatically include part of the HTML layout before the output from your script so that all your pages look the same. Because auto_prepend_file is a PHP feature, only files parsed by PHP have the file prepended; static HTML pages do not.

![](bbox=[0.128, 0.438, 0.165, 0.475])

> **HTTP Headers** After any output has been sent to the browser, you cannot use the header function to send HTTP headers or use any other PHP functions that require headers to be sent, such as session control functions or cookies. Therefore, any script included by auto_prepend_file must produce no output if you want to send custom HTTP headers.

# Error Logging

As you learned in Lesson 22 , "Error Handling," PHP allows you to configure the strictness of error reporting and the means by which it is reported.

The value of the error_reporting directive is a bitmask comprised of the values found in Table 22.1 in Lesson 22 . You can use logical operators to combine values as follows:

```
error_reporting = E_ALL & ~E_NOTICE & ~E_STRICT
```

The display_errors and log_errors directives determine whether an error is written to the screen display and web server log file, respectively.

The default settings are as follows, with errors displayed to screen and not written to a file: