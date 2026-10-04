# Introduction

path to mysql, and execute it. Then, at the prompt, create a new database.
When you're done, you should have something that looks very much like this:

```
[jay@mybox ~]$ mysql
Welcome to the MySQL monitor. Commands end with : or \g.
Your MySQL connection id is 716 to server version: 3.22.27-log
```

Type 'help' for help.

```
mysql> create database guestbook;
Query OK, 1 row affected (0.00 sec)

mysql>
```

Now, within the database named guestbook, you will need a table that stores the
user information. This table is also created in the MySQL monitor. The command to
create the table isn't very complex. You basically need to let MySQL know what
kind of information to, whether numbers or strings, and whether or not any
of the information can be omitted (when NULL). The basic command is create table; it

```
mysql> use guestbook
Database changed
mysql> create table guestbook
-> (
->  name varchar(40) null,
->  location varchar(40) null,
->  email varchar(40) null,
->  url varchar(40) null,
->  comments text null
->)
-> Query OK, 0 rows affected (0.00 sec)

mysql>
```

Now you have a database named guestbook and a table within the database
named guestbook. Now it's time to write an application in PHP that will enable you
to insert, edit, and view information in this guestbook.

# Your PHP Script

Now's the time to move to the editor. In the course of configuring your Web
server, you will need to let it know which files should be handed off to PHP so the
engine can interpret the page. Most often, these files will have a .php extension,
though it is possible to have PHP interpret anything, including html files.