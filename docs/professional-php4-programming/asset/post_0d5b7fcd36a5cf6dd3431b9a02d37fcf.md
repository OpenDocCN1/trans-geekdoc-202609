
## allow_url_fopen

This disables the opening of remote files on other web or FTP servers. If there is no need to access files from other HTTP or FTP sites then turn this off.

## Safe Mode

PHP, in an attempt to solve the shared server security problem, has a feature called safe mode. This feature limits the actions that can be performed by scripts, thus limiting the damage possibly malicious scripts can do to the server and other people's work on the server.

When safe mode is on, PHP checks if the owner of the current script is the same as the owner of any file trying to be opened. If the user ids do not match, PHP will issue a warning telling the user that this feature has been restricted.

There are several other settings that can be set in the php.ini file directly related to the behavior of safe mode. These are explained below.

## safe_mode

This directive controls whether safe mode is on or off. By default it is set to off.

## safe_mode_gid

Normally when safe_mode opens a file, the user id of the owner of the file has to be the same as the user id of the script. If you turn this on, it relaxes this slightly so only the group ids have to be the same. By default this is off.

## safe_mode_exec_dir

This directive is a list of directories where people in safe mode can execute programs. If the program is not in one of the directories in this list, the execution of the program will fail. Symlinks are resolved, so it is not possible to bypass this directive by using symlinks.

## safe_mode_allowed_env_vars

A list of prefixes for the names of environmental variables users may be set under safe mode. By default this is set to PHP_, so only environmental variables starting with PHP_ may be set.

## safe_mode_protected_env_vars

This is a list of variables that are explicitly protected under safe mode. Even if safe_mode_allowed_env_vars allows the altering of all environmental variables, this setting will stop any listed here from being changed. By default this is set to LD_LIBRARY_PATH.

## Securing MySQL

MySQL is one of the most popular open source database servers. It is worth spending a bit of time making sure it's secure. The default installation of MySQL isn't particularly secure; the steps below will help to secure it a bit more.

If you have a default installation of MySQL already, then you might want to browse to http://www.canowhoopass.com/weav/wssig/nusphere/testnusphere.php from the machine which runs MySQL.

As normal securing MySQL requires you to know exactly what you need from it and what access you need to give to the database.

## MySQL and the Root User

Running MySQL as root can have catastrophic consequences. This was one of the prime reasons why apache.org was compromised. It is best to create a mysql user or equivalent and run MySQL using the mysqld_safe wrapper under this user. This one step alone will help improve the security of MySQL massively.

To achieve this we need to make sure this non-privileged user has access to the MySQL data directories and can also execute the MySQL binary. We first need to shutdown the server; to do this issue the following command:

```
mysqladmin -p -u root shutdown
```

Presuming the data directory for mysql is located at /home/mysql/data we need to make sure these directories are only accessible to the mysql user (referred to as mysql in the following commands). We can issue the following commands at shell to make sure this is the case:

```
chown -R mysql /home/mysql/data
chmod -R go-rwx /home/mysql/data
```

If there are any symlinks within these directories make sure to run the same command on the target of the symlinks.

Also, check that the unix socket isn't within the data directory. To ensure this isn't the case use the –with-unix-socket-path configure option at compile time.

Finally restart the MySQL server. We do this using the mysqld_safe script telling it to run as user mysql:

```
mysqld_safe -user=mysql &
```

You can bypass using the user option every time you start mysql by specifying it in the my.cnf file under the [mysqld] section:

```
user=mysql
```

One more security precaution to take is to make sure that the /etc/my.cnf file is secure. Otherwise there is nothing stopping someone setting the User directive to root. The file should be owned by root but readable by everyone. The following commands should achieve this:

```
chown root /etc/my.cnf
chmod 644 /etc/my.cnf
```

## Cleaning Up

It is also a good idea to remove any fluff that has been included in the default install. This includes:

- [ ] Removing the test database
- [ ] Removing remote access
- [ ] Removing access without a username
- [ ] Making sure the root login has a password

To do this, log in to your database server from the command line:

```
mysql -u root -p
```

This should log you into your database server as the root user. If the root user has no password, the -p option should not be used, or access will not be granted. If you have problems while doing this then please refer to your MySQL documentation. Our first task is to remove the test database. We shouldn't need this at all, and as normal the fact that it is there may leave you open to attack:

```
mysql> DROP DATABASE test;
```

The above SQL command will do this for you. Now we need to clean up the allowed access a bit. MySQL uses the mysql database to store information about access privileges and other databases on the server. Thus we must select the mysql database as the one we want to work with. The following SQL will do this:

```
mysql> USE mysql;
```

We now want to finish removing the test database, remove remote access, remove access without a username, and give our root login a password:

```
mysql> DELETE FROM db WHERE Db LIKE 'test%';
```

This will remove any entries for the test database from the permissions table. We now remove remote access to the MySQL server using the following SQL command:

```
mysql> DELETE FROM user WHERE host='%';
```

Next we remove any user entries without a username:

```
mysql> DELETE FROM user WHERE User='';
```

We make sure root has a password. Make sure you pick a secure one – a mix of alphanumeric characters and punctuation marks is good:

```
mysql> UPDATE user SET Password = PASSWORD("jgt4*92smck") WHERE User = 'root';
```

Finally we need to make sure MySQL reloads its privileges tables so it recognizes the changes. We do this by issuing the following SQL command:

```
mysql> FLUSH PRIVILEGES;
```

## Managing MySQL Users

Having cleaned up our installation and made it quite secure we need to think about what access our users actually need. Most commonly it is read access to a whole database and write access to maybe one or two tables in the database; we call this user webuser. We might also have an administration PHP script protected by password authentication that needs to be able to read and write to all tables in our database; we call this user adminuser.

In this example, we presume we have a database named web site with three tables - users, news, and log_tbl. The users table is used to store information about the users who have registered at the web site. So the webuser needs SELECT, INSERT, and UPDATE permissions for this table. The news table is used to hold news items. New news items should only be able to be inserted or updated by the administrator so the webuser only needs SELECT access to this table. Finally the log_tbl table is used to log information about each hit the site gets. So both users need SELECT or INSERT access to this table, but neither user should have UPDATE or DELETE access.

We will see how to set up two users with the permissions as detailed above.

Firstly log in to the mysql server:

```
mysql -uroot -p
Enter password: ******
```

We now need to create our two users, initially we will give them both SELECT access to the entire web site database:

```
mysql> GRANT SELECT ON web site.* TO webuser@localhost IDENTIFIED BY
'secure_password';
mysql> GRANT SELECT ON web site.* TO adminuser@localhost IDENTIFIED BY
'secure_password2';
```

The webuser also needs INSERT and UPDATE privileges on the users table and INSERT privileges on the log_tbl table. We give them this using the following SQL command:

```
mysql> GRANT INSERT, UPDATE ON web site.users TO webuser@localhost;
mysql> GRANT INSERT ON web site.log TO webuser@localhost;
```

The adminuser needs INSERT, UPDATE, and DELETE privileges on the users table, INSERT and UPDATE privileges on the news table, and INSERT privileges on the log_tbl table. We do this with the following SQL commands:

```
mysql> GRANT INSERT, UPDATE, DELETE ON web site.users TO adminuser@localhost;
mysql> GRANT INSERT, UPDATE ON web site.news TO adminuser@localhost;
mysql> GRANT INSERT ON web site.log_tbl TO adminuser@localhost;
```
