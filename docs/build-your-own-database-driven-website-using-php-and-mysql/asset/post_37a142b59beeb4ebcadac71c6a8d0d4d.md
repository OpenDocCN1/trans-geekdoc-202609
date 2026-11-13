
the data from the MySQL database, then spits it out dynamically as the nicely-formatted HTML page that the browser expects. With PHP, you can write the presentation aspects of your site (the fancy graphics and page layouts) as "templates" in regular HTML. Where the content belongs in those templates, you use some PHP code to connect to the MySQL database and -- using SQL queries just like those you used to create a table of jokes in Chapter 2 -- retrieve and display some content in its place.

Just so it's clear and fresh in your mind, this is what will happen when someone visits a page on our database-driven Web site:

- The visitor's Web browser requests the Web page using a standard URL.
- The Web server software (Apache, IIS, or whatever) recognizes that the requested file is a PHP script, and so the server interprets the file using its PHP plug-in, before responding to the page request.
- Certain PHP commands (which we have yet to learn) connect to the MySQL database and request the content that belongs in the Web page.
- The MySQL database responds by sending the requested content to the PHP script.
- The PHP script stores the content into one or more PHP variables, and then uses the now-familiar `echo` function to output the content as part of the Web page.
- The PHP plug-in finishes up by handing a copy of the HTML it has created to the Web server.
- The Web server sends the HTML to the Web browser as it would a plain HTML file, except that instead of coming directly from an HTML file, the page is the output provided by the PHP plug-in.

## Connecting to MySQL with PHP

Before you can get content out of your MySQL database for inclusion in a Web page, you must first know how to establish a connection to MySQL from inside a PHP script. Back in Chapter 2, you used a program called `mysql` that allowed you to make such a connection. PHP has no need of any special program, however; support for connecting to MySQL is built right into the language. The following PHP function call establishes the connection:

```
mysql_connect(address, username, password);
```

Here, `address` is the IP address or hostname of the computer on which the MySQL server software is running ("`localhost`" if it's running on the same computer as the Web server software), and username and password are the same MySQL user name and password you used to connect to the MySQL server in Chapter 2.

You may or may not remember that functions in PHP usually return (output) a value when they are called. Don't worry if this doesn't ring any bells for you -- it's a detail that I glossed over when I first discussed functions. In addition to doing something useful when they are called, most functions output a value, and that value may be stored in a variable for later use. The mysql_connect function shown above, for example, returns a number that identifies the connection that has been established. Since we intend to make use of the connection, we should hold onto this value. Here's an example of how we might connect to our MySQL server.

```
$dbcxn = mysql_connect("localhost", "root", "mypasswd");
```

As described above, the values of the three function parameters may differ for your MySQL server. What's important to see here is that the value returned by mysql_connect (which we'll call a connection identifier) is stored in a variable named $dbcxn.

Since the MySQL server is a completely separate piece of software, we must consider the possibility that the server is unavailable, or inaccessible due to a network outage, or because the username/password combination you provided is not accepted by the server. In such cases, the mysql_connect function doesn't return a connection identifier (since no connection is established). Instead, it returns false. This allows us to react to such failures using an if statement:

```
$dbcxn = @mysql_connect("localhost", "root", "mypasswd");
if (!$dbcxn) {
    echo( "<p>Unable to connect to the ".
    "database server at this time.</p>" );
    exit();
}
```

There are three new tricks in the above code fragment. First, we have placed an @ symbol in front of the mysql_connect function. Many functions, including mysql_connect, automatically display ugly error messages when they fail. Placing an @ symbol in front of the function name tells the function to fail silently, allowing us to display our own, friendlier error message.

Next, we put an exclamation point in front of the $dbcxn variable in the condition of the if statement. The exclamation point is the PHP negation operator, which basically flips a false value to true, or a true value to false. Thus, if the connection fails and mysql_connect returns false, !$dbcxn will evaluate to true, and cause the statements in the body of our if statement to be executed. Alternatively, if a connection was made, the connection identifier stored in $dbcxn will evaluate to true (any number other than zero is considered "true" in PHP), so !$dbcx will evaluate to false, and the statements in the if statement will not be executed.

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

## Sending SQL Queries with PHP

In Chapter 2, we connected to the MySQL database server using a program called mysql that allowed us to type SQL queries (commands) and view the results of those queries immediately. In PHP, a similar mechanism exists: the mysql_query function.

```
mysql_query(query, connection_id);
```

Here query is a string that contains the SQL command we want to execute. As with mysql_select_db, the connection identifier parameter is optional.

What this function returns will depend on the type of query being sent. For most SQL commands, mysql_query returns either true or false to indicate success or failure respectively. Consider the following example, which attempts to create the Jokes table we created in Chapter 2:

```
$sql = "CREATE TABLE Jokes (
 ID INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
 JokeText TEXT,
 JokeDate DATE NOT NULL
 )";
if ( @mysql_query($sql) ) {
 echo("<p>Jokes table successfully created!</p>");
} else {
 echo("<p>Error creating Jokes table: " .
 mysql_error() . "</p>");
}

```

Again, we use the @ trick to suppress any error messages produced by mysql_query, and instead print out a friendlier error message of our own. The mysql_error function used here returns a string of text that describes the last error message that was sent by the MySQL server.

For DELETE, INSERT, and UPDATE queries (which serve to modify stored data), MySQL also keeps track of the number of table rows (entries) that were affected by the query. Consider the SQL command below, which we used in Chapter 2 to set the dates of all jokes that contained the word "chicken":

```
$sql = "UPDATE Jokes SET JokeDate='1990-04-01'
 WHERE JokeText LIKE '%chicken%'"

```

When we execute this query, we can use the mysql_affected_rows function to view the number of rows that were affected by this update:

```
if ( @mysql_query($sql) ) {
 echo("<p>Update affected " . mysql_affected_rows() .
 " rows.</p>");
} else {
 echo("<p>Error performing update: " . mysql_error() .
 "</p>");
}

```

SELECT queries are treated a little differently, since they can retrieve a lot of data, and PHP must provide ways to handle that information.

## Handling SELECT Result Sets

For most SQL queries, the mysql_query function returns either true (success) or false (failure). For SELECT queries this just isn't enough. You'll recall that SELECT queries are used to view stored data in the database. In addition to indicating whether the query succeeded or failed, PHP must also receive the results of the query. As a result, when it processes a SELECT
