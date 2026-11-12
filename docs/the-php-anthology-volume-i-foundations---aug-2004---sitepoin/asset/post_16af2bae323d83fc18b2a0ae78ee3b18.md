
Again, the answer is simple with PHP: use the mysql_query function combined with SQL commands INSERT and UPDATE. INSERT is used to create new rows in a table, while UPDATE is used to modify existing rows.

## Inserting a Row

A simple INSERT, using the articles table defined at the start of this chapter, looks like this:

```
// A query to INSERT data
$sql = "INSERT INTO
articles
SET
title = '$title',
body = '$body',
author = '$author'";

// Run the query, identifying the connection
if (! $queryResource = mysql_query($sql, $dbConn)) {
trigger_error('Query error ' . mysql_error() . ' SQL: ' . $sql);
}
```

## Updating a Row

Before you can use an UPDATE query, you need to be able to identify which row(s) of the table to update. In this example, I’ve used a SELECT query to obtain the unique article_id value for the article entitled “How to insert data”:

```
// A query to select an article
$sql = "SELECT article_id FROM articles
WHERE title='How to insert data'";

if (! $queryResource = mysql_query($sql, $dbConn)) {
trigger_error('Query error ' . mysql_error() . ' SQL: ' . $sql);
}

// Fetch a single row from the result
$row = mysql_fetch_array($queryResource, MYSQL_ASSOC);

// A new title
$title = 'How to update data';

$sql = "UPDATE
 articles
 SET
 title='Title'
 WHERE
 article_id='' . $row['article_id'] . ''";

 if (!$queryResource = mysql_query($sql, $dbConn)) {
  trigger_error('Query error ' . mysql_error() . ' SQL: ' . $sql);
 }
```

In the above example, we used the SELECT query to find the ID for the row we wanted to update.

In practical Web applications, the UPDATE might occur on a page which relies on input from the Web browser, after the user has entered the value(s) using an HTML form, for example. It is possible that strings in this data might contain apostrophes, which would break the SQL, and impact upon security. In light of this, make sure you read “How do I solve database errors caused by quotes/apostrophes?”, which covers SQL injection attacks.

![](img/5b6cdf7cf4cf53e30b19e047895dc464_101_0.png)

## Beware Global Updates

Be careful with UPDATE and remember to use a WHERE clause to indicate which rows to change.

For example, consider this query:

```
UPDATE articles SET title = 'How NOT to update data'
```

This will update *every* row of the table!

## Another Class Action

Using the MySQL class last seen in “How do I fetch data from a table?”, we can perform INSERT and UPDATE queries without any further modifications. Repeating the above examples using the class, we can first INSERT like this:

```
// Connect to MySQL
$db =& new MySQL($host, $dbUser, $dbPass, $dbName);

$title = 'How to insert data';
$body = 'This is the body of the article';
$author = 'HarryF';

// A query to INSERT data
$sql = "INSERT INTO
        articles
        SET
        title = '$title',
        body = '$body',
        author = '$author'";

$db->query($sql);

if (!$db->isError()) {
    echo 'INSERT successful';
} else {
    echo 'INSERT failed';
}
```

We can UPDATE as follows:

```
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

// A query to select an article
$sql = "SELECT article_id FROM articles
        WHERE title='How to insert data'";

$result = $db->query($sql);

$row = $result->fetch();

// A new title
$title = 'How to update data';

$sql = "UPDATE
        articles
        SET
        title='' . $title . ''
        WHERE
        article_id='' . $row['article_id'] . ''";

$db->query($sql);

if (!$db->isError()) {
    echo 'UPDATE successful';
} else {
    echo 'UPDATE failed';
}
```

## How do I solve database errors caused by quotes/apostrophes?

Consider the following SQL statement:

```
INSERT INTO articles SET title='The PHP Anthology';
```

Perhaps the PHP script that made this query contained something like this:

```
<?php
$title = "The PHP Anthology";

$sql = "INSERT INTO articles SET title='$title'; ";

$result = mysql_query($sql, $dbConn);
?>
```

No problem so far, but look what happens if we change the title:

```
$title = "PHP's Greatest Hits";
```

Notice the apostrophe in the title? When we place this in the SQL statement,
the query MySQL receives will be as follows:

```
INSERT INTO articles SET title='PHP's Greatest Hits';
```

See the problem? When MySQL reads that statement, it will only get as far as
this:

```
INSERT INTO articles SET title='PHP'
```

The rest of the statement will cause a syntax error and the query will fail. It's
easy enough to avoid this problem when you write the title yourself, but what
happens when your script gets the value from user input?

## The Great Escape

The solution is to **escape** the apostrophe character by adding a backslash before
the apostrophe. The following query, for example, will work:

```
INSERT INTO articles SET title='PHP\'s Greatest Hits';
```

## Backslashes and the ANSI SQL Standard

Note that using the backslash as an escape character is not standard ANSI SQL. If MySQL is the only database you'll ever use, the backslash may be acceptable, but the same SQL statement run on another database may well fail. According to ANSI SQL we should escape apostrophes with another single apostrophe:

```
INSERT INTO articles SET title='PHP ''s Greatest Hits';
```

The question is, how do we make sure all our apostrophes are escaped when we build a query on the fly in PHP? Dealing with this situation has become rather confusing due to the number of alternative solutions:

- First we have the php.ini setting magic_quotes_gpc. Magic quotes is a feature of PHP which, when turned on, automatically escapes single and double quotes, as well as backslashes and null characters found in incoming GET, POST and cookie variables, by adding backslashes to the strings. This may sound great, but in practice it quickly makes for trouble, typically where forms are involved.

Say you have a form which is used for editing articles. Your script takes the text the user enters and inserts it into MySQL. Now, if the user fails to complete some important field, you might want to re-display the details that have been entered in the form so far. With magic quotes on you'd have to strip out all the slashes it added to the values (with PHP's stripslashes function)!

Then, what if you wanted to run the code on a server where magic_quotes_gpc is disabled? Your code would then have to check to see if magic quotes is switched on and bypass the use of stripslashes. Headaches are inevitable, and if you make a mistake and end up with spurious backslashes stored in your database⁴, you may have a painful cleanup process ahead of you.

Magic quotes is discussed in some detail in Chapter 1. If you do switch off magic_quotes_gpc as I advise, you should be aware of the potential risks to security. See the section called “SQL Injection Attacks” below and Appendix C.

⁴It continually amazes me how many professionally designed sites fail to handle character escaping properly! Keep an eye out for unexpected backslashes in your own Web travels. See Chapter 1 for my advice on how best to avoid this on your own sites.

- Next, we have the PHP function addslashes. Applied to any string, addslashes will use backslashes to escape single quotes, double quotes, backslashes and null characters. This makes it an effective means to escape strings for use in queries.

If magic quotes is on, of course, you must not use addslashes, or characters would be escaped twice! To solve this conflict, you can check if magic quotes is enabled with the function get_magic_quotes_gpc, which returns TRUE if magic quotes is enabled and FALSE if it isn't. You can bundle up this test with a function as follows:

```
<?php
function safeAddSlashes($string)
{
if (get_magic_quotes_gpc()) {
return $string;
} else {
return addslashes($string);
}
}
?>
```

- The third way, which is very similar to addslashes, uses the function mysql_escape_string or mysql_real_escape_string (the latter was added in PHP 4.3.0). These functions use the underlying MySQL C++ API (provided by the developers of MySQL, rather than the developers of PHP) to escape special characters.

These functions escape null characters, line feeds, carriage returns, backslashes, single quotes, double quotes, and end-of-file characters. Since PHP 4.3.0, both functions have used the current character set for the connection between PHP and MySQL. There is, therefore, no difference between these two functions in the latest PHP versions, so feel free to stick with the shorter of the two, mysql_escape_string, if your server is up-to-date.

As this method is, in effect, the built-in mechanism provided by MySQL for escaping strings, I recommend it over addslashes or magic_quotes_gpc. Of course, if you want your SQL to port well to other databases, you may want to consider “hiding” the function call within a class method, which allows you to swap out the class—including the escape mechanism—when moving to a different database.
