
FIGURE 1.24
The sample PHP file as seen in Dreamweaver CS3

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_53_0.png)

You can now open this file in your Web browser, as seen in Figure 1.25.

http://localhost/info.php

If you prefer, you can create a custom PHP file to test whether PHP is properly running, such as the following:

```
<?php
print "Hello, World! This is PHP.";
?>
```

When you run this file in the browser, you should see your message displayed.

FIGURE 1.25

PHP information displayed in a Web browser

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_54_0.png)

## Installing PHP for UNIX

Installing PHP for UNIX is more detailed and requires more configuration. This is true for most command-line installation setups. You can download the installer files from the book’s Web site or one of the official PHP Web sites.

After you obtain the PHP installer files, you can begin the process of installation. Before you begin the installation, it is a good idea to stop Apache to ensure none of the files becomes corrupted.

```
/usr/local/apache/bin/apachectl stop
```

To start the installation, create the directory where PHP will be installed.

```
mkdir /usr/local/php5
```

You can substitute php5 for simply php. However, adding the version number makes it easier to have multiple installations and will be easier to manage in the future.

```
cd /usr/local/php5
```

Unpack the files and type the installation directory:

```
gunzip php-5.2.5.tar.gz
tar -xvf php-5.2.5.tar
cd php-5.2.5
```

## Building configuration parameters

The next step is to build the config line. This will contain all the necessary extensions and features you want to include in the installation. For example, you need to include database and image support to complete some of the chapters in this book, among others. Each option is contained within a set of single quotes (‘’) and will include the path if necessary.

```
./configure' '--prefix=/usr/local/php5' '--with-
apxs=/usr/local/apache/bin/apxs' '--with-gd' '--enable-exif' '--with-mysql=shared,/usr/local/php5' '--with-
mysqli=shared,/usr/local/php5/bin/mysql_config' '--with-
libxml-dir=shared,/usr/local/php5' '--with-
xsl=shared,/usr/local/php5' '--with-jpeg-dir=/usr/local/php5'
'--with-png-dir=/usr/local/php5' '--enable-gd-native-ttf' '--with-freetype-dir=/usr/local/php5' '--with-
gettext=shared,/usr/local/php5'
```

When the configuration process is complete (which can take a while depending on the system), create and run the installer:

```
make
make install
```

After the make install command is completed, PHP should be installed.

## Configuration

A few portions of PHP need to be configured to make sure it works seamlessly with Apache and your overall development system. This process is fairly easy to complete, but incorrect modification can result in a broken system. Also, when modifying configuration files, it is best to make a backup first.

The first step is to move the php.ini file to a central location that PHP will use when it starts up.

```
cp php.ini.recommended /usr/local/lib/php.ini
```

In order for Apache to load PHP files, add the necessary module references:

```
LoadModule php5_module modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps
```

Restart Apache to have these changes take effect. Any time you edit the values in PHP or Apache, you must restart the server.

```
/usr/local/apache/bin/apachectl start
```

With everything properly installed, you can test the setup by running a sample PHP file:

```
<?php
phpinfo();
?>
```

## Summary

In this chapter, you went through the steps necessary to install the complete development system. This process included the installation of Apache, PHP, and MySQL on a Windows or UNIX Web server. The next chapter walks you through the process of making this development setup more secure. This includes securing the files on the server as well as the overall server configuration through the httpd.conf configuration file.

## Chapter 2

## Exploring Flash and PHP

**IN THIS CHAPTER**

- Introducing the Web server
- Exploring PHP
- Exploring the basics of MySQL
- Exploring Flash

If you have installed all of the components on the server, you can configure the setup to be more secure. After security is explained, the next step is to set up the proper error handlers and look at ways to create a more usable setup for the end user.

After security and configuration of the Web server are complete, you will look at an overview of PHP to better understand how everything works. MySQL usage and basic integration with PHP are explained using various examples with descriptions and explanations.

The last section explores Flash, including class setup and overall IDE explanation.

### Introduction to the Web Server

In Chapter 1, you learned how to set up a development server, which included the installation of PHP, MySQL, and Apache. This section is an overview of how the Web server is set up, as well as how to make the system more secure.

### Working with .htaccess files

The .htaccess file is used to modify how Apache functions for a specific directory. This file is similar to the httpd.conf file found in the global configuration of Apache, with the exception that it is not required and can be globally disabled, provided the admin modifies the settings of the Web server.

The syntax of this file is not very advanced. It is basically a text file that informs the Web server of specific modifications.

For example, have you noticed a Web site that has specialized file extensions, such as the MediaTemple Web host, which has the following format?

```
http://www.mediatemple.net/contact.mt
```

Notice how the URL has a .mt extension. This extension is not a standard file extension. This modification can be achieved using the .htaccess file:

```
# use custom file extensions
AddType application/x-httpd-php .me
```

This modification can also be done using the httpd.conf file if you prefer to have the entire Web server be able to use this custom file extension.

Apache handles many requests by default and can offer even more with additional modules installed. One module in particular allows you to have custom URLs, also commonly referred to as clean URLs.

The possibilities with .htaccess are varied and totally depend on your application. One more common usage of .htaccess is to redirect www and non-www requests to the same location. This not only limits redundant links but also provides better search engine optimization.

An example of this conversion, using the domain example.org, would look something similar to the following:

```
# Force www.domain.com to domain.com
RewriteCond %{HTTP_HOST} ^www.example.org [NC]
RewriteRule ^(.*)$ http://example.org/$1 [R=301,L]
```

## Protecting your content

You can protect your content in a number of ways. You can build a custom authentication system or use the basic authentication that is packaged with Apache.

The basic authentication is set up in two steps. The first step is to create the password and user.

You use the htpasswd file to create the password file. This password-creation command is located in the bin/ directory where you installed Apache. For example, you will most likely find the file at the following location, assuming you used the suggested installation path in Chapter 1.

```
$ /usr/local/apache/bin/htpasswd
```

The first time you create a user, you need to inform the password-creation application to create a new password file. From that point on you omit the -c flag.

Failure to remove the -c flag after the first user setup will result in a new password file and remove any existing users.

While not required, it is a good practice to periodically back up this and any other important files in case your system encounters an unexpected crash or data corruption.

The command to create a password is simply a call to the password application with the username appended to the end.

```
$ cd /usr/local/apache/bin/
$ htpasswd -c /usr/local/apache/passwd/passwords USERNAME
```

Be sure to replace USERNAME with the actual username you want to add.

The htpasswd application will ask you for the password you want to assign, and then ask you to type the same password again to confirm it.

The generated password file is encrypted. However, you should still store it in a secure location. Under no circumstances should this file be stored in the public directory because it could compromise the integrity of your system.

This isn't as important in a development system, but it is a good practice to follow all proper security steps, even in a development setup, to become familiar with them. As you continue to work on servers, security will become second nature. You should never put it off to save time.

After you create the password file, add the security check in a .htaccess in whatever location you want to password protect. For example, let's add the authentication to the entire server because this is a development server and you wouldn't want anyone viewing it.

Add the following to a new .htaccess file in the root of the Web directory.

```
AuthType Basic
AuthName "Authorization Required"
AuthUserFile /usr/local/apache/passwd/passwords
Require valid-user
```

This informs Apache that any request to this directory and below requires authorization. The last line allows any user in the password file to be able to log in.

**Require valid-user**

You can also add a specific username, but this is more difficult to maintain.

This is basic authentication so it does have various limitations. For example, you cannot modify the dialog box that displays in the user's browser. You can't modify the label values next to the input boxes and, most importantly, you cannot allow the user to log out.

If your application requires a more customized and integrated login system, it may be better to build a custom PHP/MySQL setup, depending on your requirements.
