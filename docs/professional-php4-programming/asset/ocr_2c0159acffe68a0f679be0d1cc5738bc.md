Porting this function from PostgreSQL to MySQL is simply a matter of changing the built-in function:

```
function numRows($result)
{
    // Return the number of rows in the resultset
    return(@mysql_num_rows($result));
}
```

It is only fair to warn you that not all of them are this simple. In this example, the PostgreSQL and MySQL functions are equivalent; other instances might require some fancy footwork. Many other databases (such as Oracle) do not offer a direct numRows() equivalent, so a little more work would be required to emulate the behavior in an abstract manner.

Slight differences in functionality also cause problems. For example, the pg_fetch_object() function requires a row number, whereas mysql_fetch_object() and sybase_fetch_object() do not. In this case, you would either need to change the number of arguments the function accepts or keep track of the current row in some other way (perhaps with a static variable). And again, Oracle doesn't even have a fetch_object() function (OCIFetchInto() is a distant relative). No one ever said that changing database systems would be easy.

# A Database Abstraction Layer

For our own database abstraction layer we'll create a SQL class to contain our database functions, because object-oriented programming is more fun and pays better than procedural programming, and because it offers a bit more flexibility.

The disadvantage of the object-oriented approach is chiefly its slight lag in performance – PHP is not optimized for object-oriented code. If speed is of top priority, then it is best to use a procedural (function-based) approach like PHP's built-in dbx() functions. Refer to the online documentation for details. If speed is less of an issue and you favor clean, maintainable code, then an object-based solution is right for you.

Also bear in mind that it is not necessary to build your own database abstraction layer at all, as several excellent ones already exist on the web free for download, including:

+   - PEAR (http://pear.php.net/)
+   - PHPLIB (http://phplib.sourceforge.net/)
+   - MetaBase (http://phpclasses.UpperDesign.com/browse.html/package/20/)
+   - ADODB (http://php.weblogs.com/adodb/)

We're just doing it for practice.

# Building the DB Class

We start by creating a new class named DB. We'll define it in a file called DB.php.

This version of the class will be written using the MySQL functions. By wrapping the functions within the DB class, however, we end up exposing an abstract API to our application code. The application won't have to know that the underlying database is a MySQL database, with the exception of the SQL queries that get executed (because, as we learned, some SQL statements can be database-specific).