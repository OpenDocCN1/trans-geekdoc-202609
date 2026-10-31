
- **Reload_priv** — Most of the privileges granted by this column are not covered in the course of this book. This privilege is most often used with the `mysqladmin` utility to perform flush commands. See the MySQL online manual for more details.
- **Shutdown_priv** — Allows the user to shut down the daemon using `mysqladmin shutdown`.

## db table

For database-specific permissions, the db table is where you will be doing most of your work. The following is a list of columns from the db table:

```
mysql> show columns from db;
+---------------+---------------+------+-----+---------+-------+
| Field         | Type          | Null | Key | Default | Extra |
+---------------+---------------+------+-----+---------+-------+
| Host          | char(60)      |      | PRI |         |       |
| Db            | char(32)      |      | PRI |         |       |
| User          | char(16)      |      | PRI |         |       |
| Select_priv   | enum('N','Y') |      |     | N       |       |
| Insert_priv   | enum('N','Y') |      |     | N       |       |
| Update_priv   | enum('N','Y') |      |     | N       |       |
| Delete_priv   | enum('N','Y') |      |     | N       |       |
| Create_priv   | enum('N','Y') |      |     | N       |       |
| Drop_priv     | enum('N','Y') |      |     | N       |       |
| Grant_priv    | enum('N','Y') |      |     | N       |       |
| References_priv | enum('N','Y') |      |     | N       |       |
| Index_priv    | enum('N','Y') |      |     | N       |       |
| Alter_priv    | enum('N','Y') |      |     | N       |       |
+---------------+---------------+------+-----+---------+-------+
13 rows in set (0.01 sec)

mysql>
```

This works like the user table, except that permissions granted here will only work for the database specified in the db column.

## tables_priv and columns_priv

These two tables look pretty similar, and to save a bit of space, I'll only show the tables_priv table.

```
mysql> show columns from tables_priv;
+---------------+---------------+------+-----+---------+-------+
| Field         | Type          | Null | Key | Default | Extra |
+---------------+---------------+------+-----+---------+-------+
+-------------+----------+-----+-----+-----+-----+
| Host        | char(60) |     | PRI |     |     |
| Db          | char(60) |     | PRI |     |     |
| User        | char(16) |     | PRI |     |     |
| Table_name  | char(60) |     | PRI |     |     |
| Grantor     | char(77) |     | MUL |     |     |
| Timestamp   | timestamp(14) | YES |     | NULL |     |     |
| Table_priv  | set('Select','Insert','Update',
|             | 'Delete','Create','Drop','Grant',
|             | 'References','Index','Alter') |     |     |     |
|             |     |     |     |     |
| Column_priv | set('Select','Insert',
|             | 'Update','References') |     |     |     |
+-------------+----------+-----+-----+-----+-----+
8 rows in set (0.00 sec)
```

For users who only get access to a table or set of tables within a database, the exact rights will be stored in this table. Note the use of the set column type for table_priv and column_priv tables. All of the rights available to a specific user will be crammed into these two cells.

![](img/de0823012275cf4ceebdb822a56e6b71_469_0.png)

> At a couple of points in the course of this book, we advised against using the set column type. In fact the db table is a good example of where set makes sense. There are few potential values for the column and the number of potential values is not likely to change.

## Grant and Revoke Statements

Since the tables discussed above are regular MySQL tables, you can alter them with the SQL statements you are already familiar with. But consider the nightmare that would be. If you wanted to grant a new user table-level access, you would first need to insert a row into the user database with an SQL statement that looked like this:

```
INSERT INTO user (Host, User, Password, Select_priv, Insert_priv, Update_priv, Delete_priv, Create_priv, Drop_priv, Reload_priv, Shutdown_priv, Process_priv, File_priv, Grant_priv, References_priv, Index_priv, Alter_priv) VALUES ('localhost', 'juan', 'password', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N')
```

Then you'd need to grant specific rights with another insert statement to another table.

If you are thinking you could script these functions with a Web front end, that is definitely a possibility. But you'd want to be very careful, because the script would have the equivalent of root access to the database, which could be very unsafe.

Happily, the MySQL has some built-in statements that make user administration a whole lot easier. Knowing the grant and revoke statements will save you from having to send individual queries.

### Grant

Before we get into specifics of this statement, take a look at the statement that would grant all rights on the database named guestbook to user jim; jim's password will be pword.

```
mysql> grant all on guestbook.* to jim@localhost
identified by "pword";
```

This command will make all the necessary changes to the user and db tables.

The first part of the grant statement can take the word all, or it can take any of the options listed in the user table. Most often, you will be granting rights to use SQL statements (select, create, alter, delete, drop, index, insert, and update).

The second portion (on guestbook in the example) identifies where privileges will be applied: universally, to a single database, to tables, or to columns. Table D-1 shows how to indicate where privileges should be applied.

TABLE D-1 PERMISSION LEVEL

| Identifier | Meaning |
|---|---|
| grant all on *.* | Universal rights; inserted into the user table |
| grant all on database.* | Applies to all tables in a single database |
| grant all on database.table_name | Rights apply to a single table |
| grant all(col1, col2) on database.table_name | Rights apply only to specific columns in a specific database and table. |

The third portion (to jim@localhost in the example) indicates the user to be given access. As we mentioned earlier, MySQL needs both a name and a host. In the grant statement, these are separated by the @ symbol.

Finally the identified by portion gives the user a password.
Here are a few more examples of grant statements.

```
grant select, update, insert  on guestbook2k.guestbook to
alvin@localhost identified by "pword";
```

The preceding statement allows alvin to view, update, and insert records into the table guestbook in database guestbook2k.

```
grant select, update (name, url)  on guestbook2k.guestbook to
chipmunk@localhost identified by "Mel12068";
```

With the preceding statement, the user can only view and update two columns (name and URL). No deletes or inserts allowed.

```
grant all on *.* to josh@localhost identified by "pword";
```

The preceding statement gives this user all privileges. This means that josh@localhost is even allowed to grant privileges to other users.

### Revoke

If you want to remove some of a user's privileges, you can use the revoke statement. To remove shutdown privileges from a user who had been granted all privileges, like josh above, you could run the following:

```
revoke Shutdown on *.* from josh@localhost;
```

Notice that the word from is used in the revoke statement in place of to. Otherwise revoke works just like grant.

Note that to remove a user entirely you must run a delete statement against the user table. Since the user is identified by a name and host, the following should do it:

```
delete from user where user='user' and host='host'
```

### Viewing grants

Starting in version 3.23.4, MySQL incorporated the show grants statement, which allows you to see the exact grants available at a given time. All you need to know is the user name and host.

```
mysql> show grants for jayg@localhost;
+----------------------------------------------------------+
| Grants for jayg@localhost                                |
+----------------------------------------------------------+
```
