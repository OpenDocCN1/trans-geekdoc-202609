the GD library installed on their local machines.) The GD library is a standard part of PHP as of version 4.3, but you need to make sure PHP is configured to use it.

To configure the library on a Linux computer, you need to go through the standard configuration process, including a --with-gd option. You can find out more about this process at www.php.net/manual/en/installation.php.

To configure the library on a Windows computer with a prebuilt PHP installation, you need to edit the php.ini file, found in the C:\Windows directory. (If the file isn't there, you can copy the php.ini-dist file found in the PHP installation directory to the Windows directory, renaming it C:\Windows\php.ini.) Then you need to modify the extension_dir line as follows:

```
extension_dir = C:/Program Files/PHP/php-4.3.0-Win32/
extensions/
```

Or use whatever path contains your PHP installation. In this entry, the extensions/ directory follows the PHP installation path.

Then remove the semicolon on the following line:

```
;extension=php_gd.dll
```

to get

```
extension=php_gd.dll
```

Then restart the Apache server.

![](bbox=[0.02, 0.63, 0.1, 0.72])

The creator of the GD graphics library, Boutell.Com, is continually revising the product and issuing new versions at www.boutell.com/gd/. The latest version as of this writing is version 2.0, which includes a significant number of new features. The online manual for the PHP image library at www.php.net/image includes many functions that rely on GD version 2.0. If your PHP installation has an older version of GD, check whether the functions you want to use require the newest version. Functions that require 2.0 will display a message such as the following on their Web documentation page (www.php.net/imagecopyresampled is the Web documentation page for the imagecopyresampled function, for example):

Note: This function was added in PHP 4.0.6 and requires GD 2.0.1