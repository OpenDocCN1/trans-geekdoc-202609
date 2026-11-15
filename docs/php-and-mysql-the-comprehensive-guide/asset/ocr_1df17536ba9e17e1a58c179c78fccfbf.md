of type E_DEPRECATED. As already mentioned, PHP 8.x no longer supports the old extension (nor does PHP 7):

```
extension = mysqli # for the mysqli extension
 extension = php_mysql.dll # for the deprecated mysql extension
```

You also need the client library for MySQL. Fortunately, this is already included and is called mysqli.nd. In the output of phpinfo(), you will also find an entry for mysqli.nd, even if you have not activated the MySQL extension.

Under Unix/Linux, the extension is integrated into most binary packages of the distributions. If you want to compile it yourself, you need the --with-mysql=/path/to/mysql configuration switch for the mysql extension. This extension requires the special program mysql_config, which provides and also accepts configuration options. The corresponding switch is then called --with-mysql=/path/to/mysql_config. You therefore need the complete path to the program here, including the program name.

It is then worth calling phpinfo() (or php -m) again to see whether the extension is active. Figure 19.8 shows the output under PHP 8.3. Incidentally, the PDO extension for MySQL is called pdo_mysql, not pdo_mysqli.

![](bbox=[0.141, 0.443, 0.92, 0.831])

Figure 19.8 The “improved” MySQL Extension in the Output of “phpinfo()”