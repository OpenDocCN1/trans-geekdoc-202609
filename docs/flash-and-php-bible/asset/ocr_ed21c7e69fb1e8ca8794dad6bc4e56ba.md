Unpack the files and type the installation directory:

```
gunzip php-5.2.5.tar.gz
tar -xvf php-5.2.5.tar
cd php-5.2.5
```

# Building configuration parameters

The next step is to build the config line. This will contain all the necessary extensions and features you want to include in the installation. For example, you need to include database and image support to complete some of the chapters in this book, among others. Each option is contained within a set of single quotes (‘’) and will include the path if necessary.

```
./configure' '--prefix=/usr/local/php5' '--with-
apxs=/usr/local/apache/bin/apxs' '--with-gd' '--enable-exif' '--with-mysql=shared,/usr/local/php5' '--with-
mysqli=shared,/usr/local/php5/bin/mysql_config' '--with-
libxml-dir=shared,/usr/local/php5' '--with-
xsl=shared,/usr/local/php5' '--with-jpeg-dir=/usr/local/php5'
'--with-png-dir=/usr/local/php5' '--enable-gd-native-ttf' '---
with-freetype-dir=/usr/local/php5' '--with-
gettext=shared,/usr/local/php5'
```

When the configuration process is complete (which can take a while depending on the system), create and run the installer:

```
make
make install
```

After the make install command is completed, PHP should be installed.

# Configuration

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