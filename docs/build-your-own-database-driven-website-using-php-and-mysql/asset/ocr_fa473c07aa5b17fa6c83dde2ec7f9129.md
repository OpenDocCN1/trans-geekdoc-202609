considered "true" in PHP), so ! $dbcx will evaluate to false, and the statements in the if statement will not be executed.

The last new trick is the exit function, which is the first example that we’ve encountered of a function that takes no parameters. All this function does is cause PHP to stop reading the page at this point. This is a good response to a failed database connection, because in most cases the page will be unable to display any useful information without that connection.

As in Chapter 2, the next step, once a connection is established, is to select the database you want to work with. Let's say we want to work with the joke database we created in Chapter 2. The database we created was called jokes. Selecting that database in PHP is just a matter of another function call:

```
mysql_select_db("jokes", $dbcx);
```

Notice we use the $dbcx variable that contains the database connection identifier to tell the function which database connection to use. This parameter is actually optional. When it's omitted, the function will automatically use the link identifier for the last connection opened. This function returns true when it's successful and false if an error occurs. Once again, it's prudent to use an if statement to handle errors:

```
if ( ! @mysql_select_db("jokes") ) {
    echo( "<p>Unable to locate the joke " .
    "database at this time.</p>" );
    exit();
}
```

Notice that this time, instead of assigning the result of the function to a variable and then checking if the variable is true or false, I have simply used the function call itself as the condition. This may look a little strange, but it's a very commonly used shortcut. To check if the condition is true or false, PHP executes the function and then checks its return value – exactly what we need to happen.

With a connection established and a database selected, we are now ready to begin using the data stored in the database.

# Sending SQL Queries with PHP

In Chapter 2, we connected to the MySQL database server using a program called mysql that allowed us to type SQL queries (commands) and view the results of those queries immediately. In PHP, a similar mechanism exists: the mysql_query function.

```
mysql_query(query, connection_id);
```

Here query is a string that contains the SQL command we want to execute. As with mysql_select_db, the connection identifier parameter is optional.