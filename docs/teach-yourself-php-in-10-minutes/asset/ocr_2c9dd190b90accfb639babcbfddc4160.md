# # The Command-Line Environment

In order to use PHP from the command line, you need to have a PHP executable installed on your system. When running in a web environment, PHP is usually installed as an Apache module, but it is also possible to build a standalone program called `php` that can be used as a command-line interface (CLI).

# ## Differences Between CLI and CGI Binaries

Beginning in version 4.2, PHP started to differentiate between binary programs intended for CGI and those for CLI use. Both executables provide the same language interpreter, but the CLI version includes the following changes to make it more suitable for command-line use:

+   - No HTTP headers are written in the output.
+   - Error messages do not contain HTML formatting.
+   - The `max_execution_time` value is set to zero, meaning that the script can run for an unlimited amount of time.

To find out whether a `php` binary is a CGI or CLI version, you can run it with the `v` switch to see its version information. For instance, the following output is from the CLI version PHP 5.0.3:

```
PHP 5.0.3 (cli) (built: Dec 15 2004 08:07:57)
Copyright (c) 1997-2004 The PHP Group
Zend Engine v2.0.3, Copyright (c) 1998-2004 Zend Technologies
```

The value in parentheses after the version number indicates the Server Application Programming Interface (SAPI) that is in use. You can also find this value dynamically in a script by looking at the return value from the function `php_sapi_name` .

![](bbox=[0.116, 0.7, 0.166, 0.745])

**Windows Distributions** The Windows distributions of PHP 4.2 included two binariesthe CGI version was called `php.exe` , and the CLI binary was `php-cli.exe` . For PHP 4.3, both were called `php.exe` , but they were found in folders called `cli` and `cgi` , respectively.

For PHP 5 and higher, `php.exe` is the CLI version, and now the CGI binary is named `php-cgi.exe` . A new `php-win.exe` CLI binary is also included that runs silentlythat is, the user doesn't need to open a command prompt window.