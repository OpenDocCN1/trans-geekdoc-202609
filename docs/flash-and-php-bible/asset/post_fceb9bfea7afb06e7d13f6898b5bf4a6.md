
## Gathering information about Apache

As you continue to work with Apache, there are some commands and tools that can result in more time to develop an application instead of micromanaging the server.

### Starting and stopping Apache

Sometimes Apache can act up just like any other piece of software or hardware on your system. Oftentimes when this occurs, a simple restart will fix the issue. For instance, as more users request files from Apache, it can start to fill up internal memory and temporary files.

To restart Apache you can simply call the following command in UNIX from the command line or restart the service on Windows:

```
$ /usr/local/apache/bin/apachectl restart
```

> NOTE The path to the apachectl application can vary depending on the installation of Apache.

If you want to stop Apache and not have it restart, use the following command. This would most likely be done when installing new modules or updating Apache itself.

```
$ /usr/local/apache/bin/apachectl stop
```

To start the server again after you complete the update, simply use the start option:

```
$ /usr/local/apache/bin/apachectl start
```

### Determining the version of Apache

Occasionally, when installing new software, you need to know which version of Apache you are currently running. For example, when installing PHP you need to know which version of Apache you are using. This is found by running a simple command switch.

```
$ /usr/local/apache/bin/httpd -V
```

The result of that command would be something similar to Figure 2.1.

### Determining which modules are installed in Apache

You can very easily determine which modules are currently installed in Apache by using the following command-line flags in UNIX.

```
$ /usr/local/apache/bin/apachectl -t -D DUMP_MODULES
```

To determine the modules in Windows, you would run the following command:

```
httpd -t -D DUMP_MODULES
```

FIGURE 2.1
Displaying the current version of Apache

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_62_0.png)

An example response from this command is something similar to the following:

Loaded Modules:
core_module (static)
mpm_worker_module (static)
http_module (static)
so_module (static)
include_module (shared)
deflate_module (shared)
log_config_module (shared)
env_module (shared)
expires_module (shared)
headers_module (shared)
setenvif_module (shared)
ssl_module (shared)
mime_module (shared)
status_module (shared)
autoindex_module (shared)
info_module (shared)
vhost_alias_module (shared)
negotiation_module (shared)
dir_module (shared)
imagemap_module (shared)
actions_module (shared)
userdir_module (shared)
alias_module (shared)
rewrite_module (shared)
...
Syntax OK

If you omit the -D DUMP_MODULES flag you will only see the Syntax response. This informs you if something is wrong or tells you everything is okay.

```
$ /usr/local/apache/bin/apachectl -t
```

For Windows the command would be

```
httpd -t
```

## Using custom error documents

When you view a URL on a Web site, Apache serves a page to you based on your request. By default, if Apache is asked to serve a file it can't find, it returns an ugly 404 page that is not very informative and actually causes a potential security concern.

As you can see in Figure 2.2, Apache has printed the server information for the world to see. Now this isn't a huge security concern, but every piece of information can add up to a major problem.

FIGURE 2.2
Default error page from Apache

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_63_0.png)

A more important issue with using the standard error pages is the fact the user is presented with a useless page. For example, the user now knows the file doesn't exist, but has nowhere to go and no idea what could be the problem. Oddly enough, if a user is shown a 404 page he or she will usually not stick around, and that means an abandoned user for your site.

## Modifying Apache

Luckily, Apache allows you to modify this default error page. Some hosts allow you to modify the file using the included control panel that they installed when you purchased the server. In this case, however, the development server requires you to manually configure the majority of it.

Using custom error documents is as simple as adding the modification to a .htaccess file. This file is usually stored in the Document Root to ensure all files will see the file.

The following code is the syntax required to modify the error document.

```
# Customized Error Handler
ErrorDocument 204 /error.html
ErrorDocument 301 /error.html
ErrorDocument 302 /error.html
ErrorDocument 400 /error.html
ErrorDocument 401 /error.html
ErrorDocument 403 /error.html
ErrorDocument 404 /error.html
ErrorDocument 500 /error.html
ErrorDocument 501 /error.html
ErrorDocument 502 /error.html
ErrorDocument 503 /error.html
```

As you can see, the error documents will be replaced by one file. You can, of course, point to a separate file for each error encountered. If you do not assign a specific error page, Apache reverts to its default. The previous list is a robust record of possible error codes, but it is not a complete one.

### Dynamic error documents

Using PHP, you can create a dynamic error handling system. The idea is to call one page like you did in the previous example, with the exception that a variable will be passed along to notify that page of which error was encountered.

You start by modifying the error handler in the .htaccess file, such as:

```
# Error Handler, request is sent to a php file
ErrorDocument 204 /errorHandler.php?e=204
ErrorDocument 301 /errorHandler.php?e=301
ErrorDocument 302 /errorHandler.php?e=302
ErrorDocument 400 /errorHandler.php?e=400
ErrorDocument 401 /errorHandler.php?e=401
ErrorDocument 403 /errorHandler.php?e=403
ErrorDocument 404 /errorHandler.php?e=404
ErrorDocument 500 /errorHandler.php?e=500
ErrorDocument 501 /errorHandler.php?e=501
ErrorDocument 502 /errorHandler.php?e=502
ErrorDocument 503 /errorHandler.php?e=503
```

That code tells Apache to redirect those errors to the errorHandler.php file, passing in the error code. The next step is to build the PHP file that will handle the error codes. This PHP will expect one argument and will be smart enough to return a valid response if no error is passed in.

The first part of the file captures the error code and initializes a variable to store the error string.

```php
<?php
$errorCode = $_GET['e'];
$errorString = "";
...
?>
```

When an error code is found, a check to make sure it is a valid number is made to keep the application secure.

```php
<?php
$errorCode = $_GET['e'];
$errorString = "";
if(!is_numeric($errorCode))
{
$errorCode = -1;
}
...
?>
```

A basic switch is used to determine which error code was encountered. Switches are explained in the section “Exploring the Basics of PHP” later in this chapter.

```php
<?php
$errorCode = $_GET['e'];
$errorString = "";
if(!is_numeric($errorCode))
{
$errorCode = -1;
}
switch($errorCode)
{
case 204: // No Content (Empty Document)
$errorString = "No Content (Empty Document)";
break;
case 301: // Moved Permanently
$errorString = "Moved Permanently";
break;
case 400: // Bad Request
$errorString = "Bad Request";
break;
case 401: // Unauthorized User
$errorString = "Unauthorized User";
break;
case 403: // Forbidden
$errorString = "Forbidden";
break;
case 404: // Document Not Found
$errorString = "Document Not Found";
break;
case 500: // Internal Server Error
$errorString = "Internal Server Error";
break;
case 503: // Out of Resources
$errorString = "Out of Resources";
break;
case -1: // No Error Code
$errorString = "Unknown Error";
}
?>
```

The last step is to display the error string to the user, which completes the custom error handling script. You will notice that some of the error codes were omitted from the switch to demonstrate the fact that the script silently moves on if an invalid error code is displayed.

```php
<?php
$errorCode = $_GET['e'];
$errorString = "";

if(!is_numeric($errorCode))
{
$errorCode = -1;
}
```
