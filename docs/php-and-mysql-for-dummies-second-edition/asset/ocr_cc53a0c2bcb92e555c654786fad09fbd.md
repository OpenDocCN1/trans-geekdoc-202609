# 9. Unpack the tarball by typing

```
gunzip -c filename | tar -xvf -
```

For example:

```
gunzip -c mysql-3.23.44.tar.gz | tar -xvf -
```

You see a new directory named mysql-version — for instance, mysql-4.0.15.

You must be using an account that is allowed to create files in /usr/local.

# 10. Change to the new directory.

For instance, type cd mysql-4.0.17.

# 11. Type the following:

```
./configure --prefix=/usr/local/mysql
```

You see several lines of output. The output will tell you when configure is done. This might take some time.

# 12. Type make.

You see many lines of output. The output will tell you when make is done. make might run for some time.

# 13. Type make install.

make install will finish quickly.

*Note:* You might need to run this command as root.

# 14. Type the following:

```
scripts/mysql_install_db.
```

This command runs a script that initializes your MySQL databases.

# 15. Make sure that the ownership and group membership of your MySQL directories are correct. Set the ownership with these commands:

```
chown -R root /usr/local/mysql
chown -R mysql /usr/local/mysql/data
chgrp -R mysql /usr/local/mysql
```

These commands make root the owner of all the MySQL directories except data and make mysql the owner of data. All MySQL directories belong to group mysql.

# 16. Set up your computer so that MySQL starts automatically when your machine starts by copying the file mysql.server from /usr/local/mysql/support-files to the location where your system has its startup files.