# Configuring Apache for PHP

Before the Apache server can run PHP examples it must be told where to find the PHP module and how to recognize PHP files. This is achieved by editing the Apache configuration file located at C:\Apache\conf\httpd.conf.

Open the "httpd.conf" configuration file in a text editor, then find the section containing the "AddModule" directives. At the end of that section add the following three lines:

```
LoadModule php5_module c:/php/php5apache.dll
AddModule mod_php5.c
AddType application/x-httpd-php .php .phtml
```

The first two lines identify the PHP module. The final line defines a MIME type for files ending with a file extension of ".php" and ".phtml" so they will be processed by the PHP parser on request. Save the file to include these newly added configuration directives.

![](bbox=[0.289, 0.503, 0.936, 0.816])

> MIME is an acronym for "Multipurpose Internet Mail Extensions"—is a standard for defining file formats.

Rebooting your system now will ensure that the MySQL, PHP and Apache services get started with all the configuration changes applied and ready to be tested.