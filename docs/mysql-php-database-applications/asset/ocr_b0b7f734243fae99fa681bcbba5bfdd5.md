By default MySQL uses port 3306 and keeps the all-important socket file at /tmp/mysql.sock. This is generally okay: PHP looks for the socket file in this location. However, if you have multiple installations of MySQL you need to change the port and socket location, which can be a pain. You need to play with your my.cnf file. See Chapter 4 of the MySQL manual for more information.

# PHP/Apache

On Unix, PHP is loaded as an Apache module. Thus, the installation of the two must be done in concert. Once again you have many, many installation options. You can create PHP as an executable for use with CGI or command-line processing, as a shared Apache module (apxs), or for DSO. Here we cover only installation as an Apache module (except for OS X, which is discussed later in the appendix).

Start by unpacking both Apache and PHP.

```
gunzip apache_1.3.x.tar.gz
tar xf apache1.3.x.tar
gunzip php-4.2.tar.gz
tar xf php-4.2.tar.gz
```

Here x (in apache_1_3_x.tar) is the version number of Apache.
Use cd to move into the Apache directory and run configure, specifying the path to the directory in which you want to install Apache. You should be probably be running as the root account before you do this.

```
./configure --prefix=/path/to/apache
```

This prepares Apache to set up machine-specific information that PHP needs to compile. You come back later and finish up the Apache installation.
Then move to the directory holding PHP. Here you find a variety of flags you might or might not wish to specify. We suggest using the following:

```
./configure --with-mysql=/path/to/mysql --enable-trans-sid
```

Here, the two flags do the following:

+   • --with-mysql — Since the MySQL client libraries are no longer distributed as part of PHP, the MySQL extension is not enabled by default. You need to use this flag and, if you have installed MySQL somewhere other than the default location, specify the directory where it can be found.

+   • --enable-trans-sid — This option allows the session ID to be included automatically in URLs after a session is started. The Shopping Cart application in Chapter 14 makes use of this option.