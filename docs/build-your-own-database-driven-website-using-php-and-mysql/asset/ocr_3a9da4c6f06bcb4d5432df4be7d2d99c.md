Note in the query that, since there are columns named ID in both tables, you must specify the name of the table when you refer to the ID column in the Authors table (Authors.ID). If you don’t specify the table name, MySQL won’t know which ID you’re referring to, and will produce this error:

```
mysql> SELECT LEFT(JokeText,20), Name, Email
-> FROM Jokes, Authors WHERE AID = ID;
ERROR 1052: Column: 'ID' in where clause is ambiguous
```

Now that you know how to efficiently access the data stored in your two tables, you can rewrite the code for your joke list to take advantage of joins.
The following is reproduced with complete error checking (which has been
omitted here for brevity) in jokelist2.php in the code archive (located at
http://www.sitepoint.com/books/).

```
$jokelist = mysql_query(
"SELECT JokeText, Name, Email
FROM Jokes, Authors WHERE AID=Authors.ID");
while ($joke = mysql_fetch_array($jokelist)) {
$joketext = $joke["JokeText"];
$name = $joke["Name"];
$email = $joke["Email"];
}
// Display the joke with author information
echo( "<p>$joketext<br />" .
"(by <a href='mailto:$email'>$name</a>)</p>" );
}
```

The more you work with databases, the more you’ll come to realize how
powerful this simple ability to combine data contained in separate tables into
a single table of results really is. Consider, for example, the following query,
which displays a list of all jokes written by Joan Smith:

```
mysql> SELECT JokeText FROM Jokes, Authors WHERE
-> Name="Joan Smith" AND AID=Authors.ID;
```

The results that are output from the above query come only from the Jokes
table, but the query uses a join to let it search for jokes based on a value stored
in the Authors table. There will be plenty more examples of clever queries like
this throughout this book, but hopefully this example alone illustrates that the
practical applications of joins are many and varied, and in almost all cases can
save you a lot of work!

# Simple Data Relationships

The best type of database layout for a given situation is usually dictated by
the type of relationship that exists between the pieces of data that it needs to
store. In this section, I’ll examine the typical relationship types, and explain
how best to represent them in a relational database.