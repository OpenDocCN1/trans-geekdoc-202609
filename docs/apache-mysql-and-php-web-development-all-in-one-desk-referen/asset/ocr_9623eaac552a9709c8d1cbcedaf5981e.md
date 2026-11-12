End users simply see a Web page in their browsers. They do not see the PHP code access the MySQL database. In fact, they probably don't even know whether the database you're using is MySQL, and they probably don't know that you're using a database system. (The PHP part is a bit of a giveaway because the .php filename extension is in the URL.)

Here is a short example of a .php file that connects to a database. (For this example I'm using the database, username, password, and tables described at the beginning of this chapter.) This example uses a select statement to retrieve a row from the category table:

```
<html><title>Categories!</title>
<body>
<?php
mysql_connect("localhost", "phpuser", "phppass");
$result = mysql_query(
"select * from phpbase.category
where categoryID = 3"
);
if ($result) {
if (mysql_num_rows($result) > 0) {
$row = mysql_fetch_assoc($result);
$id = $row["categoryID"];
$name = $row["category_name"];
print "$id $name<br>\n";
}
mysql_free_result($result);
}
mysql_close();
?>
</body></html>
```

When you open this file in the browser, you see the following output:

3 books

The output is nothing fancy, but this example shows you how to connect to a database. This first line inside the PHP code does the connecting:

```
mysql_connect("localhost", "phpuser", "phppass");
```

The first parameter is the name of the host you want to connect to; this will almost always be localhost. Remember, the PHP processor runs on the same computer as the Web server and normally that's where you'll find the MySQL installation as well. Thus, "localhost" refers to the computer where PHP is running.