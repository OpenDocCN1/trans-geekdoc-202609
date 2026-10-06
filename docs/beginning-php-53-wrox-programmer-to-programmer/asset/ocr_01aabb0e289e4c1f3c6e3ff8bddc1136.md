Creating additional MySQL users is outside the scope of this book, but you can find out how to do it in the Account Management Statements section of the MySQL manual (http://dev.mysql.com/doc/refman/5.1/en/account-management-sql.html).

The mysql program stores a list of your most recent entries. For security reasons, it's a good idea to delete this list once you've set the root password, because the password will appear in the SET PASSWORD FOR lines lines in this list. To do this on Ubuntu and Mac OS X, exit the command-line tool and delete the .mysql_history file in your home directory (rm - ~/.mysql_history). On Windows, exit the command-line tool then close the Command Prompt.

> By the way, if you are not comfortable with the command-line tool, many graphical applications are available that you can use administer and talk to your MySQL server. Try the free MySQL Administrator and Query Browser programs, available from http://dev.mysql.com/downloads/gui-tools/5.0.html A good Web-based tool is phpMyAdmin (http://www.phpmy.net/), which also comes with WampServer on Windows (click the WampServer icon to access it).

# A Quick Play with MySQL

Now you've set up the MySQL root user, you can start working with databases. In the following sections, you create a new database, add a table to the database, and add data to the table. You will learn how to query databases, update data in tables, and delete data, tables, and databases.

> Most of the examples in the following sections show commands, statements, and other SQL keywords being entered all-lowercase letters. Though SQL keywords are traditionally used in uppercase, MySQL also lets you enter keywords in lowercase. Use lowercase if you prefer.

# Creating New Database

It's easy to create a new MySQL database. First, fire up the MySQL command-line tool using the same method that used when changing the root password. Open a shell prompt, change to the correct folder (if you using Windows or Mac OS X), and then on Ubuntu or Windows type:

```
mysql -u root -p
```

On the Mac type:

```
./mysql -u root -p
```

Press Enter. Now enter the root password you specified earlier, and press Enter again. You should see the prompt appear:

```
mysql>
```

To create a new database, all you have to do is use the CREATE DATABASE command. Type the following to create a new database called mysatabase:

```
CREATE DATABASE mysatabase;
```