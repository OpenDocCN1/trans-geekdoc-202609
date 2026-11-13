# The Host Environment

Now let's look at how PHP interacts with the web server's host environment.

# Detecting the Host Platform

Because different types of systems have different sets of host commands available, if you are writing a script that could potentially be executed on different platforms, it's useful to detect what kind of web server is being used.

The constant PHP_OS contains a string that represents the operating system. The most common reason for checking this is to find out whether a script is running on a Windows platformafter all, most Unix-like systems, and even Mac OS, behave in a very similar way.

The value of PHP_OS on a Windows web server could be Windows , WINNT , or WIN32 , and in the future, other PHP_OS may come into existence. Therefore, to test for a Windows platform, you should perform a non-case-sensitive comparison on the first three characters of the string. The following condition shows just one of the ways you can do this:

```
```php
if (strtoupper(substr(PHP_OS, 0, 3)) == "WIN") { ... }
```
```

Darwin Be cautious to check only that the value of PHP_OS begins with WIN , as modern versions of Mac OS report themselves as Darwin .

# Environment Variables

The $_ENV super-global contains an element for each environment variable present. Environment variables are values from the underlying operating system, and those available to PHP are from the environment in which PHP and your web server is running.

The PATH environment variable provides your system with a list of locations to search for an executable program. Each location is checked in turn until the program is found or there are no more locations left to try, when an error occurs.

Finding the current value of the path is as simple as using the following statement:

```
```php
echo $_ENV["PATH"];
```
```