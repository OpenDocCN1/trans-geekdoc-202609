![](bbox=[0.116, 0.136, 0.208, 0.207])

The *addr* includes a port number that is needed for the connection. Almost always, the port number is 3306. On rare occasions, the MySQL administrator needs to set up MySQL to connect on a different port. In these cases, the port number is required for the connection. The port number is specified as *hostname:portnumber*. For instance, you might use *localhost:8080*.

With these statements, `mysql_connect` attempts to open a connection to the named computer, using the account name and password provided. If the connection fails, the program stops running at this point and sends *message* to the browser.

The following statement connects to the MySQL server on the local computer by using a MySQL account named *catalog* that does not require a password:

```
```php
$connection = mysql_connect("localhost","catalog","")
    or die ("Couldn't connect to server.");
```
```

![](bbox=[0.131, 0.394, 0.209, 0.466])

For security reasons, it’s a good idea to store the connection information in variables and use the variables in the connection statement, as follows:

```
```php
$host="localhost";
$user="catalog";
$password="";
$connection = mysql_connect($host,$user,$password)
    or die ("Couldn't connect to server.");
```
```

In fact, for even more security, you can put the assignment statements for the connection information in a separate file in a hidden location so that the account name and password aren’t even in the program. I explain how to do this in Chapter 10.

The variable `$connection` contains information that identifies the connection. You can have more than one connection open at a time by using more than one variable name. A connection remains open until you close it or until the program ends. You close a connection as follows:

```
```php
mysql_close($connectionname);
```
```

For instance, to close the connection in the preceding example, use this statement:

```
```php
mysql_close($connection);
```
```

# ## Selecting the right database

After the connection to the MySQL server is established and open, you need to tell MySQL which database you want to interact with. Use the `mysql_select_db` function as follows: