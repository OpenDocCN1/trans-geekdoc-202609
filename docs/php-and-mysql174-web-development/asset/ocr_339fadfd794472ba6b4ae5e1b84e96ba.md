# Installing Apache, PHP, and MySQL Under UNIX 605

The compulsory piece of MySQL housekeeping is deleting any anonymous accounts that\may be part of the distributed database. Opening a command prompt and typing the following
lines accomplish this task:

```
# mysql -u root -p
Enter password:
mysql> use mysql
mysql> delete from user User='
mysql> quit
```

You then need to type

```
# mysqladmin -u root -p reload
```

for these changes to take effect. (You should be prompted for your password).
At this point you have a working secured installation of MySQL that you can use with PHP.

# Installing PHP and Apache

Please note that in the examples below, the word VERSION is used as a placeholder for the
recent version of the software available to you. The installation process does not differ from
version to version. When running the commands, substitute VERSION with the specific
version number of the software you have downloaded.

Before installing PHP, let's get a vanilla version of Apache configured and installed so that
PHP install process can find everything related to Apache. Don't worry, we will come back to
t topic of fully configuring and installing Apache in this section. First, ensure you are in
the directory that contains the source-distribution.

```
# cd /usr/src
# sudo gunzip httpd-VERSION.tar.gz
# sudo tar -xvf httpd-VERSION.tar
# cd httpd-VERSION
# sudo ./configure --prefix=/usr/local/apache2 --enable-so
```

The second configuration flag is present to make sure mod_so will be compiled into
Apache. This module, named for the UNIX shared object (*.so) format, ensures the use of
dynamic modules such as PHP with Apache.

Let's continue the build process by isuing the following commands:

```
# sudo make
# sudo make install
```

At this point, a basic version of Apache is configured on your system. To continue preparing
to build PHP, you will need to build the additional libraries that PHP and Apache will use in our
example (JPEG, PNG, zlib, OpenSSL, and IMAP) so that the PHP build configuration properly
points to those libraries.