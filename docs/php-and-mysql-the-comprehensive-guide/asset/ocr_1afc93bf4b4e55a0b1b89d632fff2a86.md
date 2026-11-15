You can check whether it is installed in Windows 10/11 under Turn Windows Features on or off.

If IIS is missing, click it. Double-click to open further options. It is important that ISAPI and CGI are also installed under Application Development Features.

+   Apache for Windows is the Windows port of the web server market leader. The latest versions belong to the 2.x branch. The binaries for both versions can be found at https://httpd.apache.org and, officially recommended by the PHP project, at https://www.apachealounge.com/download.

If you have installed the web server, you can usually access it locally via http://localhost/ or via http://127.0.0.1/. All PHP examples in this book are located in the php sub-folder. The URL for this is then as follows:

```
http://localhost/php/
```

If you use a port other than the default port 80 for the web server, you must also specify the port must also be specified:

```
http://localhost:8080/php/
```

# Installation Packages

As Apache, PHP, and MySQL (or, alternatively, MariaDB) are often used together, some projects offer an automatic installer. A big plus is that you can uninstall the entire installation package again. However, some of the packages lag a little behind newer PHP versions, especially for PHP 8.3 (although a lot may have happened between the time these lines were written and the time you read them). Here are three of what we consider to be the best installation packages currently available:

+   XAMPP is certainly the best-known project (https://www.apachefriends.org/index.html). It has the great advantage that it is available for Linux, Windows, and macOS. The installation includes not only all extensions, but also a ready-to-use PEAR.4 it's also updated very regularly. You can also find old versions at http://sourceforge.net/projects/xampp/files. The configuration of XAMPP is not optimal for productive operation, so it is primarily used as a local development platform. The project has not been updated for PHP 8.3 yet, though (see Figure 2.3). Incidentally, XAMPP installs MariaDB, not MySQL, which initially has no significant functional impact.

+   EasyPHP Devserver (www.easyphp.org) is available for both development and production operation. With this package, the PHP versions are very easy to configure, and additional packages can also be installed. (At the time of publication, only PHP 7 was included in the current version 17.0; however, PHP 8.3 is available as an additional component for installation.)

+   The originally French project WampServer (https://www.wampserver.com/en) is also quite well known. (At the time of publication, PHP 8.3 was already supported.)

4 More on this in Section .