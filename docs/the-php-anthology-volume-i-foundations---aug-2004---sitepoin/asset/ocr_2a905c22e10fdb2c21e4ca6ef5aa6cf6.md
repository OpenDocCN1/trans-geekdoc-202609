The point of using a class here is to get some practice using PHP's object model to deal with common tasks. If you're new to object oriented programming with PHP, the most important thing to remember at this stage is that you don't need to understand all the code you find in a class to be able to use it in your code.

We'll be making use of this class and others throughout the book to illustrate how object oriented programming aids the reuse of code and can save time when you're developing applications.

# How do I fetch data from a table?

Being connected to a database is nice, sure. But what good is it if we can't get anything from it?

There are a number of ways to fetch data from MySQL, but the most widely used is probably mysql_fetch_array in conjunction with mysql_query.

We just need to add a little more to the connectToDb function we saw in “How do I access a MySQL database?” to fetch data from this table:

```
// Connect to MySQL
$dbConn = &connectToDb($host, $dbUser, $dbPass, $dbName);

// A query to select all articles
$sql = "SELECT * FROM articles ORDER BY title";

// Run the query, identifying the connection
$QueryResource = mysql_query($sql, $dbConn);

// Fetch rows from MySQL one at a time
while ($row = mysql_fetch_array($QueryResource, MYSQL_ASSOC)) {
	echo 'Title: ' . $row['title'] . '<br />';
	echo 'Author: ' . $row['author'] . '<br />';
	echo 'Body: ' . $row['body'] . '<br />';
}
```

Essentially, there are three steps to getting to your data:

+   1. First, place the necessary SQL query³ in a string:

³If you are unfamiliar with Structured Query Language (SQL), I'll cover the basics throughout this chapter. For a more complete treatment, however, refer to Build Your Own Database Driven Website Using PHP & MySQL, 2nd Edition (ISBN 0-9579218-1-0).