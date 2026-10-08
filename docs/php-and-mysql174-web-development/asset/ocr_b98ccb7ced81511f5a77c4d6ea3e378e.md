You should then enter your password. If all goes well, you should see a response something like this:

Welcome to the MySQL monitor. Commands end with; or \g.
Your MySQL connection id is 559

Server version: 5.6.19-log MySQL Community Server (GPL)

Copyright (c) 2000, 2014, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective\owners.

Type 'help'; or \h for help. Type \c to clear the current input statement.
mysql>

On your own, if you don't get a response to this, make sure that you have
run mysql_install_db if you get asked the root password, and you've typed it in
connection. If it's not correct, make sure that you typed the password correctly.

You should be at a MySQL command prompt, ready to create the database. If you are
using your own machine, follow the guidelines in the next section. If you use somebody
else's machine, these steps should already have been done for you. You can jump ahead to
to the "Using the Right Database" section. You might want to read the intervening sections
for general background, but you cannot run the commands specified there. (Or at least
soun't be able to.)

# Creating Databases and Users

The MySQL database system can support many databases. You will generally have one
database per application. In the Book-O-Rama example, the database will be called books.

Creating the database is the easiest. At the MySQL command prompt, type

```
mysql> create database db;
```

You should substitute the name of the database you want to create for dbname. To begin
creating the Book-O-Rama example, create a database called books.

That's it. You should see a response like this (the time to execute will likely be different):

```
Query OK, 1 row affected (0.0 sec)
```

This means everything has worked. If you don't get this response, make sure that you typed the
 semicolon at the end of the line. A semicolon tells MySQL that you are finished, and it should
actually execute the command.