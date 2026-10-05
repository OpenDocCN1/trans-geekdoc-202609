# Introduction to PHP

# Timeout

This value sets the default number of seconds before any HTTP request will time out. If you set PHP's max_execution_time to longer than this value, PHP will keep grinding away but the user may see a 404 error. In safe mode, this value will be ignored; you must use the timeout value in php.ini instead

> Remember

You can associate any file extension with PHP like .php3, .php5 or .htm.

# DocumentRoot

DocumentRoot designates the root directory for all HTTP processes on that server. It looks something like this on Unix – DocumentRoot /usr/local/apache_1.3.6/htdocs. You can choose any directory as document root.

# AddType

The PHP MIME type needs to be set here for PHP files to be parsed.
AddType application/x-httpd-php .php
AddType application/x-httpd-phpps .php3
AddType application/x-httpd-php3 .phtml
AddType application/x-httpd-php .html

# Action

You must uncomment this line for the Windows apxs module of Apache with shared object support –nLoadModule php4_module modules/php4apache.dll
or on Unix flavors –nLoadModule php4_module modules/mod_php.so