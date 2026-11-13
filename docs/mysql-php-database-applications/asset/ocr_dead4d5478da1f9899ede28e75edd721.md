Here are a few quick examples:

```
if ($var == 1 && $var2 <= 5 && !empty($var3))
{
    //do some stuff
}
```

Since this is a book dealing with MySQL databases, we'll show some examples of if statements you can use when playing with database queries.

To test if a select query returned any rows, you can use either of the following:

```
$query = "select * from my_table";
$result = mysql_query($query) or
die(mysql_error());
if (mysql_num_rows($result) > 0)
{
    //do something here.
}
```

```
//this would also work
$query = "select * from test.foo";
$result=mysql_query($query);
if (!($row = mysql_fetch_assoc($result)))
{
    echo "there were no rows to fetch, so the query must have returned no rows.";
}
```

The following tests if an update query actually changed anything. A similar construct would work for delete statements.

```
$query = "update mytable set coll='my text' where id = 1";
mysql_query($query) or
die(mysql_error());
if (mysql_affected_rows() == 0)
{
    echo "query did nothing";
}
```

As is noted in Chapter 3, be careful to remember that the “equal to” operator is = in MySQL, but == in PHP. A common typo is to write if ($a = $b) ... in PHP. This assigns the value of $b to $a, and always tests as true, so it can be easy to miss.