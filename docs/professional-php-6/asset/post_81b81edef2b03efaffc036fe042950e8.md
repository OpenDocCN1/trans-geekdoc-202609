
- The rich environment for writing stored procedures and functions far surpasses the limited environment offered by MySQL 5, and supports standard programming languages such as Perl and even PHP itself for writing stored procedures, unlike the proprietary languages used by SQL Server and Oracle; and the vast array of libraries for more complex functions such as Geographic Information Services makes it far superior to many of the other alternatives for enterprise-class database services.

- It's great all around. In addition to being free and standards-compliant, it's also extremely fast, extremely stable, and pretty easy to set up and install. It's also very well supported by PHP, which is a huge bonus, given the topic of this book.

## The Installation Itself

Now that you understand the background, it’s time to start the installation. The following assumes that you have a working UNIX machine, installed and ready to go.

If you don’t already have a UNIX machine and want a good place to start, GNU/Linux is the ideal UNIX-based operating system for PC-based hardware. Just make sure to tell it to install all the developer utilities during installation, because you’ll need these to get PHP up and running.

This installation assumes that your UNIX machine is networked, has a private IP address assigned, and can be pinged from your workstation (and your workstation from it). It is also assumed that you are familiar with basic UNIX commands and utilities.

If all this looks good to you, then you can get started. Log in to your UNIX machine as root (or become root from a normal user account using su), and you can begin.

## Downloading and Installing PostgreSQL

Because your development environment is for your own use only, you don’t need to worry about putting PostgreSQL on a separate machine. You can use the same machine to run Apache, PHP, and your database without any real performance implications.

Mac OS X users have it easy, and need not follow this section. Instead, download the wizard-driven installer from http://www.postgresql.org/download/macosx which will install, configure and start PostgreSQL for you with virtually no intervention required.

Ensure that you get the complete archive of PostgreSQL from www.postgresql.org and that you download the source code — not any binaries. You’ll compile it yourself for maximum speed and resilience. The filename of your downloaded file will look something like postgresql-8.3.3.tar.gz. To find the URL, go to www.postgresql.org, click Downloads, and find the link for the source code.

You can download the file using Lynx or FTP if you must, but the authors’ preferred route is wget:

```
# wget ftp://ftp.postgresql.org/pub/latest/postgresql-8.3.3.tar.gz
```

After you’ve downloaded it, unpack PostgreSQL in the normal way:

```
# tar -xzvf postgresql-8.3.3.tar.gz
```

This will create a directory called postgresql-8.3.3 that contains the source files for PostgreSQL. Change into that directory:

```
# cd postgresql-8.3.3
```

Run the configure script to generate a Makefile appropriate to your particular UNIX environment:

```
# ./configure
```

With luck, you won't see any errors and you'll get a string of checks passed, with the last line reading as follows or similarly:

```
config.status: linking ./src/makefiles/Makefile.linux to src/Makefile.port
```

If this all looks good, you can start the compilation process by simply typing the following:

```
# make
```

It may take quite a while for PostgreSQL to compile, so go have a cup of coffee at this point. When you return, PostgreSQL should have compiled without incident (it is hoped), and you can install it as follows:

```
# make install
```

Strictly speaking, PostgreSQL is now installed, but a certain amount of configuration is still required. You must create the user account under which the daemon will run, set permissions on the data directory so that user owns it, and then initialize the data directory. Follow these steps to get your database working directory set up (where all your data will be stored):

```
# adduser postgres
# mkdir /usr/local/pgsql/data
# chown postgres /usr/local/pgsql/data
# su - postgres
# /usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
```

You're almost ready to start the PostgreSQL daemon (server) now. One final step: You have to tell PostgreSQL from where to allow connections. Normally, this will just be from the same server or, in a pinch, from other machines on the same network.

Suppose that your server's IP address in this case is 192.168.1.1 and you want to allow access from that IP address only. Edit the file /usr/local/pgsql/data/pg_hba.conf using your favorite editor, adding this line to the very bottom of the file:

```
Host all all 192.168.1.1 255.255.255.255 trust
```

Save the file and quit the editor. You can now start PostgreSQL using the following syntax:

```
# su - postgres
# /usr/local/pgsql/bin/postmaster -i -D /usr/local/pgsql/data &
```

The first line is very important. The postmaster process must run as your new postgres user and not as root or whoever you may have been logged in as. The -i directive when starting is important too, because it tells PostgreSQL to allow TCP/IP connections — something it disallows by default.

That’s it. You can create a database as follows, again as the user postgres:

```
# /usr/local/pgsql/bin/createdb databasename
```

Now you can manipulate it using the PostgreSQL console as follows:

```
# /usr/local/pgsql/bin/psql databasename
```

Finally, you can create new users as follows:

```
# /usr/local/pgsql/bin/createuser username
```

This concludes your crash course in PostgreSQL installation. There are plenty of variations in the process, depending on your operating system and functional requirements. More advanced setups and further details on the required libraries are covered in the PostgreSQL documentation.

## Installing the Various Support Libraries

In an ideal world, you could now press on and install PHP and Apache. Unfortunately, life is unfair, and you’ll need to install a few support libraries for PHP.

PHP 6 has drastically reduced the number of external libraries needed to get the core functionality up and running. The major GNU/Linux distributions have also become much better at handling binary distributions of these libraries, and, for the first time, the authors now recommend installing the few needed libraries from the binary distributions. Install the following using your favorite package manager (such as yum, apt-get, and so on):

- libicu
- libicu-devel

These two libraries contain the code for the International Components for Unicode, which provide some of the software infrastructure that supports the new Unicode support in PHP 6. Which additional libraries you need (if any) depends on exactly what functionality you require.

With libicu installed, you’re ready to get onto PHP and Apache themselves.

## Installing PHP and Apache

PHP and Apache must be installed in tandem, so they are covered in one section here. It will become clear exactly why very shortly.

Mac OS X users can once again bail out at this step, and download and install MAMP from http://www.mamp.info/en/index.php. It will create a working PHP 6 installation for you using a simple ‘wizard’ process. Once done, you’ll find you have an installation of PHP at http://localhost:8080.

First, download the latest versions of Apache and PHP from their respective Web sites — httpd.apache.org and www.php.net.

The two files you’ll download will be named something like `httpd-2.2.9.tar.gz` and `php-6.0.0.tar.gz`. Uncompress them in the normal manner.

```
# tar -xzvf httpd-2.2.9.tar.gz
# tar -xzvf php-6.0.0.tar.gz
```

The first step is to do an initial configure on Apache. Change into the Apache directory (probably `httpd-2.2.9`) and run the configure script with the default parameters, and then compile and install:

```
# ./configure
# make && make install
```

When it’s done, go ahead and configure PHP. Change back out of the Apache directory and into the PHP directory:

```
# cd ..
# cd php-6.0.0
```

You now configure PHP using a remarkably simple `configure` statement, compared to the requirements of previous versions of PHP:

```
./configure --with-apxs2=/usr/local/apache/bin/apxs --with-pgsql --with-pdo-pgsql
```

Note that if you installed Apache to a different prefix, or used one of the `-enable-layout` options, you will need to amend the `--with-apxs2` directive to point to the installation location of the `apxs` executable.

It may well take a few minutes to configure, but assuming that you’ve followed this appendix correctly up until now, you shouldn’t receive any error messages, and everything should configure okay.

You can then build PHP:

```
# make
# make install
```

Note that the `make` may well take a few minutes, depending on the hardware and load of your server. The `make install` probably won’t take long at all. If it fails, you may need to retrace your steps. In particular, confirm that all the support packages mentioned in the previous section have been configured correctly.

The PHP compile and install process creates a module in your Apache `modules` directory; you can now configure and install Apache to make use of that module. You must tell the Apache configuration file how to handle the `.php` extension. Modify the file `/usr/local/apache/conf/httpd.conf` (again, depending on your configure parameters, this path can vary, but this is the default) and add the following lines:

```
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
```
