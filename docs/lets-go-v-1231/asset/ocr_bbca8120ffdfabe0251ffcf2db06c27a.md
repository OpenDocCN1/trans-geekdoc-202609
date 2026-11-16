# # Creating a new user

From a security point of view, it's not a good idea to connect to MySQL as the root user from a web application. Instead it's better to create a database user with restricted permissions on the database.

So, while you're still connected to the MySQL prompt run the following commands to create a new web user with SELECT, INSERT, UPDATE and DELETE privileges only on the database.

```
CREATE USER 'web'@'localhost';
GRANT SELECT, INSERT, UPDATE, DELETE ON snippetbox.* TO 'web'@'localhost';
-- Important: Make sure to swap 'pass' with a password of your own choosing.
ALTER USER 'web'@'localhost' IDENTIFIED BY 'pass';
```

Once that's done type exit to leave the MySQL prompt.

# # Test the new user

You should now be able to connect to the snippetbox database as the web user using the following command. When prompted enter the password that you just set.

```
$ mysql -D snippetbox -u web -p
Enter password:
mysql>
```

If the permissions are working correctly you should find that you're able to perform SELECT and INSERT operations on the database correctly, but other commands such as DROP TABLE and GRANT will fail.

```
mysql> SELECT id, title, expires FROM snippets;
+----+----------------------+---------------------+
| id | title                | expires             |
+----+----------------------+---------------------+
|  1 | An old silent pond   | 2025-03-18 10:00:26 |
|  2 | Over the wintry forest | 2025-03-18 10:00:26 |
|  3 | First autumn morning | 2024-03-25 10:00:26 |
+----+----------------------+---------------------+
3 rows in set (0.00 sec)

mysql> DROP TABLE snippets;
ERROR 1142 (42000): DROP command denied to user 'web'@'localhost' for table 'snippets'
```