```
echo 'Body: ' . $row['body'] . '<br />';
}
?>
```

If you’re not used to object oriented programming, this may seem very confusing, but what’s most important is to concentrate on how you can use the classes, rather than the detail hidden inside them. That’s one of the joys of object oriented programming, once you get used to it. The code can get very complex behind the scenes, but all you need to concern yourself with is the simple “interface” (API) with which your code uses the class.

**About APIs**

It’s common to hear the term API mentioned around classes. API stands for *Application Programming Interface*. What it refers to is the set of methods that act as “doors” to the functionality contained within a class. A well-designed API will allow the developer of the class to make radical changes behind the scenes without breaking any of the code that uses the class.

Compare using the MySQL classes with the earlier procedural code; it should be easy to see the similarities. Given that it’s so similar, you may ask, “Why not stick to plain, procedural PHP?” Well, in this case, it hides many of the details associated with performing the query. Tasks like managing the connection, catching errors, and deciding what format to get the query results in are all handled behind the scenes by the class. Classes also make the implementation of global modifications (such as switching from MySQL to PostgreSQL) relatively painless (i.e. you could just switch to a *PostgreSQL* class that provided the same API).

# How do I resolve errors in my SQL queries?

If something goes wrong when you try to deal with PHP and SQL together, it’s often difficult to find the cause. The trick is to get PHP to tell you where the problem is, bearing in mind that you must be able to hide this information from visitors when the site goes live.

PHP provides the `mysqli_error` function, which returns a detailed error message from the last MySQL operation performed.