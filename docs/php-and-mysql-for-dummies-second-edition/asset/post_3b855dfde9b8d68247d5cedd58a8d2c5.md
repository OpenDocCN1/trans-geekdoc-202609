
This command installs the MySQL packages. It sets the MySQL account and group name that you need, and creates the data directory at `/var/lib/mysql`. It also starts the MySQL server and creates the appropriate entries in `/etc/rc.d` so that MySQL starts automatically whenever your computer starts.

You need to be using an account that has permissions to successfully run the rpm command, such as a root account.

- 10. **To test that MySQL is running okay, type this:**

```
bin/mysqladmin --version
```

You should see the version number of your MySQL server.

## From binary files

Ready-to-use, compiled binary files are available for several flavors of Linux and Unix. If none of the flavors work for your Linux/Unix machine, you can install MySQL from source files, but it’s better to use a binary if at all possible. As of this writing, MySQL binary files were available for the following flavors of Unix, but more could be made available at any time:

- Solaris
- HP-UX
- AIX
- SCO
- SGI Irix
- Dec OSF
- QNX
- BSDi
- OpenBSD
- FreeBSD

To install a binary file version of MySQL on Linux or Unix, follow these steps:

- 1. **Point your Web browser to www.mysql.com, the MySQL home page.**
- 2. **Click the _Production_ version number link.**

Look in the list on the right side of the screen, labeled MySQL Products. Look for the section under the heading Database Server. As of this writing, the production release is 4.0.17.

- 3. **Scroll down the screen until you come to the heading for Linux or for your version of Unix (for example, Solaris Downloads).**

Each section lists several downloads for that operating system.

- 4. **Locate the correct package for your version of operating system.**

For Linux, you probably want the Intel libc6 binary version. For Unix, select the correct version of the Unix system — for example, Solaris 9 (SPARC, 64-bit).

- 5. **Click the download link for the standard version for your operating system.**

A dialog box opens.

- 6. **Select the option to save the file.**

A box opens that lets you select where you want to save the file.

- 7. **Navigate to where you want to install MySQL. Then click Save.**

The standard location is `/usr/local`; it’s best to use this location if possible.

- 8. **After the download is complete, change to the download directory — for instance, cd /usr/local.**

You see a file named `mysql-`, followed by the version number, the name of the operating system, and `.tar.gz` — for instance, `mysql-4.0.17-sun-solaris2.9-sparc-64bit.tar.gz`. This file is a tarball.

- 9. **Create a user and group ID for MySQL to run under by using these commands:**

```bash
groupadd mysql
useradd -g mysql mysql
```

The syntax for the commands might differ slightly on different versions of Unix, or they might be called `adduser` and `addgroup`.

**Note:** You must be using an account that is authorized to add users and groups.

- 10. **Unpack the tarball by typing this:**

```bash
gunzip -c filename | tar -xvf -
```

For example:

```bash
gunzip -c mysql-4.0.17-sun-solaris2.9-sparc-64bit.tar.gz | tar -xvf -
```

**Note:** You must be using an account that is allowed to create files in `/usr/local`.

- 11. **Create a link to the new directory so that you can refer to it by a shorter name, rather than its current, difficult-to-type name. Type the following:**

```
ln -s newdirectoryname mysql
```

For example:

```
ln -s mysql-4.0.17-sun-solaris2.9-sparc-64bit mysql
```

Now you can refer to the directory as mysql, instead of by its long name.

- 12. **Change to the new directory by typing cd mysql.**

You should see several subdirectories, including /bin and /scripts.

- 13. **Add the path to the bin directory (for example, /usr/local/mysql/bin) to your system path so that the MySQL programs can be accessed by any programs that need to access MySQL.**

You should do this by editing the file that sets the system variables when your computer starts up.

- 14. **Type the following:**

```
scripts/mysql_install_db
```

This command runs a script that initializes your MySQL databases.

- 15. **Make sure that the ownership and group membership of your MySQL directories are correct. Set the ownership with these commands:**

```
chown -R root /usr/local/mysql
chown -R mysql /usr/local/mysql/data
chgrp -R mysql /usr/local/mysql
```

These commands make root the owner of all the MySQL directories except data and make mysql the owner of data. All MySQL directories belong to group mysql.

- 16. **Set up your computer so that MySQL starts automatically when your machine starts by copying the file mysql.server from /usr/local/mysql/support-files to the location where your system has its startup files.**

- 17. **To test MySQL, you can start your server manually, without restarting your computer, by typing the following:**

```
bin/safe_mysqld --user=mysql &
```

- 18. **To test that MySQL is running okay, type**

```
bin/mysqladmin --version
```

You should see the version number of your MySQL server.

## From source files

Before you decide to install MySQL from source files, check for binary files for your operating system. MySQL binary files are precompiled, ready-to-install packages for installing MySQL. MySQL binary files are very convenient and reliable.

You install MySQL by downloading source files, compiling the source files, and installing the compiled programs. This process sounds terribly technical and daunting, but it’s not. Read all the way through the following steps before you begin the installation procedure.

To install MySQL from source code, follow these steps:

- 1. **Point your Web browser to www.mysql.com, the MySQL home page.**
- 2. **Click the Production version number link.**

Look in the list on the right side of the screen, labeled MySQL Products. Look for the section under the Database Server heading. As of this writing, the production release is 4.0.17.

- 3. **Scroll to the bottom of the screen to the Source Downloads heading.**

This section lists several downloads.

- 4. **Locate the tarball version and click the download link next to it.**

A dialog box opens.

- 5. **Select the option to save the file.**

A box opens that lets you select where the file will be saved.

- 6. **Navigate to where you want to install MySQL and then click Save.**

The standard location is `/usr/local`. It is best to use the standard location if possible.

- 7. **After the download is complete, change to the download directory — for instance, cd /usr/local.**

You see a file named `mysql-`, followed by the version number and `.tar.gz.` — for instance, `mysql-4.0.17.tar.gz`. This file is a *tarball*.

- 8. **Create a user and group ID for MySQL to run under by using the following commands:**

```bash
groupadd mysql
useradd -g mysql mysql
```

The syntax for the commands might differ slightly on different versions of Unix, or they might be called `adduser` and `addgroup`.

*Note:* You must be using an account that is authorized to add users and groups.

- 9. **Unpack the tarball by typing**

```bash
gunzip -c filename | tar -xvf -
```

For example:

```bash
gunzip -c mysql-3.23.44.tar.gz | tar -xvf -
```

You see a new directory named mysql-version — for instance, mysql-4.0.15.

You must be using an account that is allowed to create files in /usr/local.

- 10. **Change to the new directory.**

For instance, type cd mysql-4.0.17.

- 11. **Type the following:**

```bash
./configure --prefix=/usr/local/mysql
```

You see several lines of output. The output will tell you when configure is done. This might take some time.

- 12. **Type make.**

You see many lines of output. The output will tell you when make is done. make might run for some time.

- 13. **Type make install.**

make install will finish quickly.

*Note:* You might need to run this command as root.

- 14. **Type the following:**

```bash
scripts/mysql_install_db
```

This command runs a script that initializes your MySQL databases.

- 15. **Make sure that the ownership and group membership of your MySQL directories are correct. Set the ownership with these commands:**

```
chown -R root /usr/local/mysql
chown -R mysql /usr/local/mysql/data
chgrp -R mysql /usr/local/mysql
```

These commands make root the owner of all the MySQL directories except data and make mysql the owner of data. All MySQL directories belong to group mysql.

- 16. **Set up your computer so that MySQL starts automatically when your machine starts by copying the file mysql.server from /usr/local/mysql/support-files to the location where your system has its startup files.**
