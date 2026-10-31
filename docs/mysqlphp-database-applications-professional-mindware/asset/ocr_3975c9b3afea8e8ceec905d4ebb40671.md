Then you'd need to grant specific rights with another insert statement to another table.

If you are thinking you could script these functions with a Web front end, that is definitely a possibility. But you'd want to be very careful, because the script would have the equivalent of root access to the database, which could be very unsafe.

Happily, the MySQL has some built-in statements that make user administration a whole lot easier. Knowing the grant and revoke statements will save you from having to send individual queries.

# Grant

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