# Appendix A Installing Apache, PHP, and MySQL

To install the JPEG library, follow these steps:

```
# cd /usr/src
# sudo gunzip jpegsrc.VERSION.tar.gz
# sudo tar -xvf jpegsrc.VERSION.tar.gz
# cd jpeg-VERSION
# sudo ./configure
# sudo make
# sudo make install
```

After the final step, unless there were error messages along the way, the JPEG library should be installed in /usr/local/lib. If there were errors during the process, follow the instructions in the error message or refer to the JPEG library documentation.

Repeat the gzip, tar, configure, make, and make install for the PNG and zlib source files, and note the installation directories for each.

For installing the IMAP C-client library, you can download and build the source files in the same way, but there are some idiosyncrasies that may result in differences from system to system. We recommend you use the most recent guidelines published in the PHP manual at http://php.net/manual/en/imap.requirements.php

You might also consider simply install the precompiled package for your UNIX server, as we do on Ubuntu 14.04.

```
# sudo apt-get install liblibc-client-dev
```

With all the libraries prepared for use, let's switch back to setting up PHP. Extract the source files and change to its directory:

```
# cd /usr/src
# sudo gunzip php-VERSION.tar.gz
# sudo tar -xvf php-VERSION.tar.gz# cd php-VERSION
```

Many options are available with PHP's configure command. Use ./configure --help to determine what you want to add. In this case, let's add support for MySQL, Apache, and gd.

Note that the following is all one command. You can put it all on one line, or as shown here, using the continuation character, the backslash (\). This character allows you to type one command across multiple lines to improve readability:

The first configuration flag sets the location of the installation directory for PHP, in this case /usr/local/php. The second flag ensures that PHP is built with the native driver for MySQL.