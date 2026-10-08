will be advised accordingly. Make sure you change the database information accordingly. Don't simply copy and paste my example into your programs, as this won't work.

Having made the connection to our database, we can now access it. This takes just 4 lines of code, as follows.

```
`$query = "select id from customers";`
```

This creates our MySQL query (you should recall these from when we queried the database directly with phpMyAdmin). We store the text of the query in a variable called $query. In this example, we want to select all the id values from the customers table.

```
`$q = mysql_query($query);`
```

Now we execute the actual query. The `mysql_query` function performs the query, which we have previously stored in the $query variable. Note how we assign the result of the query to the $q variable.

```
`$total = mysql_num_rows($q);`
```

Having performed the query, we now use the `mysql_num_rows()` function, which returns the total number of database records (ie, rows) which were returned in the $q query. That is, the total number of id values. At this point we haven't actually retrieved any data. All we have is the total number of rows. Which is all we need right now, so let's display it:

```
`echo "Total number of customers in the database is " . $total;`
```

# ## Reading Data

We now have a complete PHP program which can access a MySQL database. So let's adapt it to display some real data. Change the program to the following:

```
```php
<?php

$db_host = "localhost";
$db_database = "thewebbo_hms";
$db_username = "thewebbo";
$db_password = "xyzabc123";
$dbcnx = mysql_connect($db_host,$db_username,$db_password);
mysql_select_db($db_database);

$query = "select firstname,surname from customers";
$q = mysql_query($query);
```
```