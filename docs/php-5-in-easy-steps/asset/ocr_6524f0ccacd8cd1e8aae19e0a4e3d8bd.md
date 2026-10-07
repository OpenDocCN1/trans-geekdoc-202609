# Creating a new database

MySQL databases can be created and their contents amended or queried in the MySQL monitor using Structured Query Language (SQL) commands.

The SQL command “create database database-name;” is used to create a new database.

Open the MySQL monitor then type “create database garage;” to create a new database called “garage”.

The MySQL monitor responds by confirming that the new database has been created, with the message Query OK followed by information about affected rows and time elapsed.

The names of all databases on the MySQL server can be viewed with the SQL “show databases;” command to confirm that the new database does indeed exist:

![](bbox=[0.048, 0.475, 0.275, 0.635])

```
MySQL Monitor
mysql> create database garage:
Query OK, 1 row affected (0,00 sec)
mysql> show databases;
-----------------
| Database |
-----------------
| garage |
| mysql  |
| test   |
-----------------
3 rows in set (0,00 sec)
mysql> 
```

If a database with your chosen name already exists, MySQL will not create a new database, but will respond with this error message:

ERROR1007:
Can’t create database ‘garage’. Database exists.