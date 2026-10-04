# Chapter 3

We wanted to choose only the fieldnames movie_name and movie_type because we decided we didn't care about the rest of the information contained in the table at this time. If we wanted to retrieve everything, we would simply have:

```
SELECT * FROM ...
```

but instead wrote:

```
$query=SELECT movie_name, movie_type
```

Next, we told the server from what we wanted to retrieve the information.

```
FROM movie
```

Then we gave the server the conditions of our query. In this case, we wanted to see only movies made since 1990, so we wrote:

```
WHERE movie_year>1990
```

And we asked the server to sort the results by movie type and ended our query with the PHP line:

```
ORDER BY movie_type";
```

Pretty easy, eh? Let's try to use the foreach function instead of the while function and see how it works.

# Working with PHP and Arrays of Data: foreach

We touched upon arrays in the previous chapter, but there's a handy-dandy PHP function we didn't discuss. It's the foreach function, and it is quite helpful when working with arrays of data from the database.

The foreach is similar to the while function if you're using while to scroll down through a list of results from your query. Its purpose is to apply a block of commands to execute every row in your results. It is what we use in:

The preceding code would take all the variables in the row array and list each value with a line break between them. You can see this action in Chapters 4 and 5 and get a better idea of how it can be used.

# Try It Out

In your select.php file, make the following changes (shown in bold).

```
<php
//connect to MySQL
$connect = mysql_connect("localhost", "root", "mysqlpassword") or
```