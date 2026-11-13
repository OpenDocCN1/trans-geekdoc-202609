# # Connecting to MySQL Database

# ## Opening a Database Connection

PHP provides **mysqli_connect** function to open a database connection. This function takes five parameters and returns a MySQL link identifier on success, or FALSE on failure.

# ### Syntax

```
connection mysqli_connect(server,user,passwd,new_link,client_flag);
```

| Sr.No | Parameter & Description |
| :--- | :--- |
| 1 | **server**  Optional – The host name running database server. If not specified, then default value is **localhost:3306**. |
| 2 | **user**  Optional – The username accessing the database. If not specified, then default is the name of the user that owns the server process. |
| 3 | **passwd**  Optional – The password of the user accessing the database. If not specified then default is an empty password. |
| 4 | **new_link**  Optional – If a second call is made to mysqli_connect() with the same arguments, no new connection will be established; instead, the identifier of the already opened connection will be returned. |
| 5 | **client_flags**  Optional – A combination of the following constants – \n * **MYSQL_CLIENT_SSL** – Use SSL encryption \n * **MYSQL_CLIENT_COMPRESS** – Use compression protocol |