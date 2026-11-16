

Online Library - Results

| Title | Author | Price |
|-------|--------|-------|

```php
// Connect to the MySQL server
$conn = mysql_connect('localhost', 'jon', 'secret') or die(mysql_error());

// Select the database
mysql_select_db('Library', $conn) or die(mysql_error());

// Attempt to fetch the form variables
$query = addslashes($HTTP_GET_VARS['query']);
$series = $HTTP_GET_VARS['series'];
$type = $HTTP_GET_VARS['type'];
```

The majority of the work occurs in building the SQL search string:

```php
// Query the database for the list of series
$sql = "SELECT book_title, auth_name, price " .
"FROM title, details, author, authtitle, series " .
"WHERE author.auth_ID = authtitle.auth_ID AND " .
"authtitle.ISBN = title.ISBN AND title.ISBN = details.ISBN " .
"AND details.series_ID = series.series_ID";
```

This SQL statement uses table joins to retrieve data from multiple tables. However, this SQL statement does not include any of our search terms. These are handled below. We make use of the PHP string concatenation operator to append the correct comparison to the query's WHERE clause. The search is narrowed based on the value of the $type and $query form values:

```php
// Add the search terms to the query
if (!empty($series)) {
$sql .= " AND series.series_ID = $series";
}
if (!empty($query) && !empty($type)) {
if ($type == 'isbn') {
$sql .= " AND details.ISBN = '$query'";
} elseif ($type == 'author') {
$sql .= " AND author.author_name LIKE '%$query%'";
} elseif ($type == 'title') {
$sql .= " AND title.book_title LIKE '%$query%'";
}
}
$result = mysql_query($sql, $conn);
```

Lastly, the results are displayed as rows in the HTML table:

```php
// Print the <option> rows for the <select> widget
if ($result && (mysql_num_rows($result) > 0)) {
    while ($row = mysql_fetch_assoc($result)) {
    ?>
    <tr>
    <td><u><?php echo (htmlspecialchars($row['book_title'])); ?></u></td>
    <td><?php echo (htmlspecialchars($row['auth_name'])); ?></td>
    <td><?php echo (htmlspecialchars($row['price'])); ?></td>
    </tr>
    <?php
    } else {
    echo ("<tr><td colspan=\"3\">No matches were found.</td></tr>\n");
    }
    // Close the database connection
    mysql_close($conn);
    ?>
    </table>
    <a href="search.php">Search Again</a>
    </body>
    </html>
```

Note that we break out of PHP code to display the HTML. This is not the only way to write this code; it's a matter of personal style.

This is the output of results.php:

![](img/9cf7789dba9b16ef3f8576d5aea89186_678_0.png)

That's it. You now have the beginning of a simple application that can authenticate users, present a dynamically generated search form, and display the results of a search based on variable search terms.

In search.php, the script does not check the login and password entered by the user. That is, the user can bypass the login page and use the online library system. In real-world situations, it is best to have a proper login system. For more information on secure logins, refer to Chapter 23.

## Database Abstraction

The built-in database API functions make database programming with PHP quite easy. For Oracle, use the Oracle functions; for Informix, use the Informix functions and so on.

There can be a drawback to these functions, however, if you need to change the RDBMS. If the code for the entire application is riddled with functions specific to a single database system, we would need to change and re-test the whole enchilada. This unpleasant situation can be improved by creating a database abstraction layer – a centralized body of code that handles all interaction with the database. By passing all of the SQL statements through a single point, database access is greatly simplified and sweeping changes can often be made by modifying a small set of code. The extra code may add slightly to the amount of processing that occurs with every database call, but if the abstraction layer is kept light and simple, this difference will be insignificant.

Ideally, a database abstraction layer is intended to shield the developer who uses it from having to know the details of the underlying database. In a perfect world, the developer should be able to code the entire application using standard ANSI SQL without even knowing which RDBMS lies underneath.

The reality, of course, is a bit cloudier. Variations in SQL syntax among the numerous SQL servers, as well as differences in available functionality, dash such hopes of complete RDBMS independence. Difficult choices need to be made for each project concerning whether the benefits of leveraging RDBMS specific capabilities, such as the REPLACE statement in MySQL, or the use of built-in functions, outweigh the benefits of maintaining the highest level of portability among RDBMSs.

Such decisions are typically made by determining the likelihood that the project will need to be ported. If a project uses DB2, and it is fairly certain that there are no circumstances under which it would need to be ported to a different SQL server, then it is best to take advantages of features specific to DB2. If, however, the project uses Microsoft Access and it will have to be to be upgraded to Oracle someday, then it would be wise to craft the SQL statements in a way that makes them portable, without using any features that may be unique to Microsoft Access.

Even if you do not anticipate porting your application from one RDBMS to another, a database abstraction layer is a good idea. It centralizes the application's access to the database, which results in cleaner, more manageable code. For example, if we later decided to log all of the queries for analysis, we could simply add some code to the abstraction layer that stores every SQL statement in a log file. Without an abstraction layer, this simple task would be daunting.

Some programmers abstract the database by wrapping each API specific function in a more generic function:

```php
function numRows($result)
{
    // Return the number of rows in the resultset
    return(@pg_numrows($result));
}
```

Porting this function from PostgreSQL to MySQL is simply a matter of changing the built-in function:

```php
function numRows($result)
{
    // Return the number of rows in the resultset
    return(@mysql_num_rows($result));
}
```

It is only fair to warn you that not all of them are this simple. In this example, the PostgreSQL and MySQL functions are equivalent; other instances might require some fancy footwork. Many other databases (such as Oracle) do not offer a direct numRows() equivalent, so a little more work would be required to emulate the behavior in an abstract manner.

Slight differences in functionality also cause problems. For example, the pg_fetch_object() function requires a row number, whereas mysql_fetch_object() and sybase_fetch_object() do not. In this case, you would either need to change the number of arguments the function accepts or keep track of the current row in some other way (perhaps with a static variable). And again, Oracle doesn't even have a fetch_object() function (OCIFetchInto() is a distant relative). No one ever said that changing database systems would be easy.

## A Database Abstraction Layer

For our own database abstraction layer we'll create a SQL class to contain our database functions, because object-oriented programming is more fun and pays better than procedural programming, and because it offers a bit more flexibility.

The disadvantage of the object-oriented approach is chiefly its slight lag in performance – PHP is not optimized for object-oriented code. If speed is of top priority, then it is best to use a procedural (function-based) approach like PHP's built-in dbx() functions. Refer to the online documentation for details. If speed is less of an issue and you favor clean, maintainable code, then an object-based solution is right for you.

Also bear in mind that it is not necessary to build your own database abstraction layer at all, as several excellent ones already exist on the web free for download, including:

- PEAR (http://pear.php.net/)
- PHPLIB (http://phplib.sourceforge.net/)
- MetaBase (http://phpclasses.UpperDesign.com/browse.html/package/20/)
- ADODB (http://php.weblogs.com/adodb/)

We're just doing it for practice.

## Building the DB Class

We start by creating a new class named DB. We'll define it in a file called DB.php.

This version of the class will be written using the MySQL functions. By wrapping the functions within the DB class, however, we end up exposing an abstract API to our application code. The application won't have to know that the underlying database is a MySQL database, with the exception of the SQL queries that get executed (because, as we learned, some SQL statements can be database-specific).

