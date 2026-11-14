
is allowed to select data but is not allowed to insert data. The sequence of events and errors would look like the following:

```
# mysql -h localhost -u joe -pabc123 test
Reading table information for completion of table and column
names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \\g.
Your MySQL connection id is 12 to server version: 5.0.20-log
Type 'help;' or '\\h' for help. Type '\\c' to clear the buffer.

mysql> SELECT * FROM test_table;
| id | test_field |
|----|------------|
| 1 | blah |
| 2 | blah blah |
2 rows in set (0.0 sec)

mysql> INSERT INTO test_table VALUES ('', 'my text');
Error 1044: Access denied for user: 'joe@localhost' (Using
password: YES)
```

Action-based permissions are common in applications with several levels of administration. For example, if you have created an application containing personal financial data, you might grant only SELECT privileges to entry-level staff members, but INSERT and DELETE privileges to executive-level staff with security clearances.

## Working with User Privileges

In most cases when you are accessing MySQL through an Internet service provider, you will have only one user and one database available to you. By default, that user will have access to all tables in that database and will be allowed to perform all commands. In this case, the responsibility is yours as the developer to create a secure application through your programming.

However, if you are the administrator of your own server, or if your Internet service provider allows you to add as many databases and users as you want as well as to modify the access privileges of your users, these next few sections will take you through the processes of doing so.

### Adding Users

Administering your server through a third-party application might afford you a simple method for adding users by using a wizard-like process or a graphical interface. However, adding users through the MySQL monitor is not difficult, especially if you understand the security checkpoints used by MySQL, which you just learned.

The simplest method for adding new users is the GRANT command. By connecting to MySQL as the root user, you can issue one command to set up a new user. The other method is to issue INSERT statements into all the relevant tables in the mysql database, which requires you to know all the fields in the tables used to store permissions. This method works just as well but is more complicated than the simple GRANT command. The simple syntax of the GRANT command is shown here:

```
GRANT privileges
ON databasename.tablename
TO username@host
IDENTIFIED BY "password";
```

The following are some of the common privileges you can grant. For a complete list, see the GRANT entry in the MySQL Manual at http://dev.mysql.com/doc/refman/5.0/en/grant.html.

- ALL—Gives the user all common privileges
- ALTER—User can alter (modify) tables, columns, and indexes
- CREATE—User can create databases and tables
- DELETE—User can delete records from tables
- DROP—User can drop (delete) tables and databases
- FILE—User can read and write files; this privilege is used to import or dump data
- INDEX—User can add or delete indexes
- INSERT—User can add records to tables
- PROCESS—User can view and stop system processes; only trusted users should be able to do this
- RELOAD—User can issue FLUSH statements; only trusted users should be able to do this
- SELECT—User can select records from tables
- SHUTDOWN—User can shut down the MySQL server; only trusted users should be able to do this
- UPDATE—User can update (modify) records in tables

If, for instance, you want to create a user called john with a password of 99hjcl5, with SELECT and INSERT privileges on all tables in the database called myDb, and you want this user to be able to connect from any host, use this command:

```
GRANT SELECT, INSERT
ON myDB.*
TO john@"%"
IDENTIFIED BY "99hjcl5";
```

Note the use of two wildcards: * and %. These wildcards replace values. In this example, * replaces the entire list of tables and % replaces a list of all hosts in the known world—a very long list indeed.

Here's another example of adding a user with the GRANT command, this time to add a user called jane with a password of 45sdg11, with ALL privileges on a table called employees in the database called myCompany. This new user can connect only from a specific host:

```
GRANT ALL
ON myCompany.employees
TO jane@janescomputer.company.com
IDENTIFIED BY "45sdg11";
```

If you know that janescomputer.company.com has an IP address of 63.124.45.2, you can substitute that address in the hostname portion of the command, as follows:

```
GRANT ALL
ON myCompany.employees
TO jane@"63.124.45.2"
IDENTIFIED BY "45sdg11";
```

One note about adding users: Always use a password and make sure that the password is a good one!

If you use the GRANT command to add users, the changes take immediate effect. To make absolutely sure of this, you can issue the FLUSH PRIVILEGES command in the MySQL monitor to reload the privilege tables.

### Removing Privileges

Removing privileges is as simple as adding them; instead of the GRANT command, you use REVOKE. The REVOKE command syntax is as follows:

```
REVOKE privileges
ON databasename.tablename
FROM username@hostname;
```

In the same way that you can grant permissions using INSERT commands, you can also revoke permissions by issuing DELETE commands to remove records from tables in the mysql database. However, this requires that you be familiar with the fields and tables, and it's much easier and safer to use REVOKE.

To revoke the ability for user john to INSERT items in the myCompany database, you would issue this REVOKE statement:

```
REVOKE INSERT
ON myDB.*
FROM john@"%";
```

Changes made to the data in the privilege tables happen immediately, but for the server to be aware of your changes, issue the FLUSH PRIVILEGES command in the MySQL monitor.

## Installing and Configuring Apache

In this second of three installation-related chapters, you will install the Apache web server and familiarize yourself with its main components, including log and configuration files.

### Current and Future Versions of Apache

When you visit the Apache HTTPD server website at http://httpd.apache.org, you will see announcements for releases of the Apache 1.3.x, Apache 2.0.x, and Apache 2.2.x versions. As you can imagine by the version numbers, Apache 1.3.x is the oldest of the three versions. The Apache Software Foundation maintains all three versions, but the features in Apache 2.2.x include greater support for filtering, caching, load balancing, and other system functions; it is the version used in this chapter. However, if you choose to install Apache 2.0.x or even Apache 1.3.x, all the PHP and MySQL code in this kit will still work as described. In fact, you will find a considerable number of hosting providers still using the Apache 1.3.x version of the server, as well as others hosting the Apache 2.0.x version. If you have any issues with installing Apache 2.2.x as described in this chapter, try a previous version (for example, Apache 2.0.x); the installation instructions are remarkably similar. The installation instructions in this chapter refer to Apache HTTPD server version 2.2.8, which is the best available version of the software at the time of this writing.

The Apache Software Foundation uses minor release numbers for updates containing security enhancements or bug fixes. Minor releases do not follow a set release schedule. When enhancements or fixes are added to the code and thoroughly tested, the Apache Software Foundation releases a new version with a new minor version number.

It is possible that by the time you purchase this kit, the minor version number will have changed to 2.2.9 or beyond. If that is the case, you should read the list of changes, which is linked from the download area at http://httpd.apache.org/download.cgi, for any changes regarding the installation or configuration process, which makes up the bulk of this chapter.

Although it is unlikely that any installation instructions will change between minor version updates, you should get in the habit of always checking the changelog of software that you install and maintain. If a minor version change does occur while you are reading this kit but the changelog notes no installation changes, simply make a mental note and substitute the new version number wherever it appears in the installation instructions and accompanying figures.

### Installing Apache on Mac OS X

Lucky you, Apache is already installed on Mac OS X! By default, the Apache server binary is located at /usr/sbin/httpd. Configuration files such as httpd.conf, the master configuration file for Apache, are in /etc/httpd. Because Apache is ready to go and fully prepared to use PHP, skip ahead to the “Apache Configuration File Structure” section to learn more about the Apache configuration file and how to use it.

### Installing Apache on Windows

Apache 2.2 runs on most Windows platforms and offers increased performance and stability over the Apache 2.0 and Apache 1.3 versions for Windows. You can build Apache from source, but because not many Windows users have compilers, this section deals with the MSI installer version.
