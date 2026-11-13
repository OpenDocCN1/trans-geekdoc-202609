Now on to PHP. You should have a folder into which you unzipped all the PHP files. (In the following instructions we are assuming the folder is c:\php.) Also, PHP 4 and later versions have a pretty good Apache module for Windows. In the previous version of this book we recommended using the CGI binary. The Apache module has a bit more in the way of functionality, so you should probably use that.

+   1. Copy php5ts.dll and php5apache.dll from c:\php into the c:\windows\ system or c:\winnt\system32 directory, whichever is available on your version of Windows.

+   2. Next, copy the php.ini-dist file from the c:\php directory to c:\windows on Windows 95/98, or c:\winnt or winnt40 on NT/2000/XP. Rename the file php.ini. Now open the php.ini file and change the extension_dir entry so it matches the name of the folder where you placed the .dll files. For example:

```
extension_dir = c:/windows/system32
```

+   3. Now you need to alter your Apache configuration file. The easiest way to do this is to go to the Start menu and select Apache HTTP Server → Configure Apache Server → Edit Configuration File.

+   4. Add the following three lines to the file. Note that the first line must match the name of the directory on your system:

```
LoadModule php5_module c:/windows/system
AddModule mod_php5.c
AddType application/x-httpd-php .php
```

The last line ensures that all files with .php extensions are processed as PHP applications. If you want other file extensions to by parsed by PHP, simply add another AddType line to the conf file, as follows:

```
AddType application/x-httpd-php5 .phtml
```

You may have to make a couple of other alterations to your httpd.conf file, such as the following:

+   If the server refuses to start, you may need to add something to the ServerName directive. If you are using TCP/IP in your local area network you may need to add the IP address of your machine, as follows:

```
ServerName 192.168.1.2
```

Or, if your machine is not networked, you may want to use the following ServerName:

```
ServerName 127.0.0.1
```