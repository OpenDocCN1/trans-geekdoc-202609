is allowed to select data but is not allowed to insert data.The sequence of events and errors would look like the following:

```
# mysql -h localhost -u joe -pabc123 test
Reading table information for completion of table and column
names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \\g.
Your MySQL connection id is 12 to server version: 5.0.20-log
Type 'help;' or '\\h' for help. Type '\\c' to clear the buffer.

mysql> SELECT * FROM test_table;
+----+-------------+
| id | test_field  |
+----+-------------+
|  1 | blah        |
|  2 | blah blah   |
+----+-------------+
2 rows in set (0.0 sec)

mysql> INSERT INTO test_table VALUES ('', 'my text');
Error 1044: Access denied for user: 'joe@localhost' (Using
password: YES)
```

Action-based permissions are common in applications with several levels of administration. For example, if you have created an application containing personal financial data, you might grant only SELECT privileges to entry-level staff members, but INSERT and DELETE privileges to executive-level staff with security clearances.

# # Working with User Privileges

In most cases when you are accessing MySQL through an Internet service provider, you will have only one user and one database available to you. By default, that user will have access to all tables in that database and will be allowed to perform all commands. In this case, the responsibility is yours as the developer to create a secure application through your programming.

However, if you are the administrator of your own server, or if your Internet service provider allows you to add as many databases and users as you want as well as to modify the access privileges of your users, these next few sections will take you through the processes of doing so.