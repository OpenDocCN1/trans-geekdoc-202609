
# Part II: Working with PHP

```php
} else {
    echo "You just removed $deleted_rows row/rows from the\ndatabase";
}
```

MYSQL_ERRNO() If there is a problem with a query, this function will spit out the error number registered with MySQL.

```php
int mysql_errno ([int link_identifier])
```

On its own, this isn't terribly helpful. For the most part, you would only use it if you wished to use custom error handling. Better error messages come from mysql-error() which is discussed next.

MYSQL_ERROR() This function should accompany every mysql_query() you run.

```php
string mysql_error ([int link_identifier])
```

As you can see in code samples throughout the book we make use of mysql-error with the die statement.

```php
mysql_query("select * from my_table") or
die (mysql_error());
```

Without it, you will only know that your query has failed. You won't know if you're searching for a database that doesn't exist or if you're trying to insert a string into a numeric field, or have made some sort of syntactic blunder.

MYSQL_RESULT() This function, grabs the contents of a specific cell, should be used sparingly.

```php
mixed mysql_result (int result, int row [, mixed array])
```

It's relatively slow and can always be replaced by mysql_fetch_array(). However, if you need to get data from a single cell it can be convenient. The second argument will be the number of the row you are accessing. The third can either be the numeric offset of the column or the column name.

Here's an example of how you could use mysql_result(). In this case, we're running a simple count(), so there is only one value to be accessed. Using mysql_result() is a bit easier than: mysql_fetch_array().

```php
mysql_connect("localhost", "username", "password");
mysql_select_db("test");
$result = mysql_query("select count(*) from users") or
die (mysql_error());
echo mysql_result($result,0);
```

# Chapter 6: PHP's Built-in Functions

If you have many rows, or even many columns, that need to be retrieved you should use mysql_fetch_array().

# LESS FREQUENTLY USED MYSQL FUNCTIONS

Given the title of this book, it wouldn't make too sense if we didn't cover the entire API. There are many available functions that probably won't come into play too often. But if you're going to be writing applications with these tools, it's best to know what's available.

# MYSQL_FETCH_OBJECT() This function provides another way to access data retrieved from a query.

```php
object mysql_fetch_object(int result [, , int result_type])
```

This grabs a row using mysql_fetch_array(). The only difference is that you refer to values fetched from a row as object properties. It can also take the constants MYSQL_ASSOC, MYSQL_NUM, or MYSQL_BOTH.

```php
$result = mysql_query("select distinct fname, lname from users
id=1) or
die(mysql_error($result));
$an_object = mysql_fetch_object($result);
echo "First name: " . $an_object->fname;
echo "Last name: " . $an_object->lname;
```

We discuss the object-oriented approach in Chapter 7.

![](img/245156cc770929860a3ede93c01f9981_153_0.png)

There are two reasons you might want to use this function. First, you love working with OO syntax and wish to extend it to your database calls. The second reason is relevant to the Perl hackers out there.

PHP 4, like Perl printing, which we discussed in Chapter 4 under the discussion of delimiting strings. "Here" printing may not work on Windows installations.

![](img/245156cc770929860a3ede93c01f9981_153_1.png)

# Part II: Working with PHP

When using Here printing, you can print only simple variables – arrays. However, object properties are allowed. Thus, the following would work:

```php
print <<EQ0>
field value is $am_object->name;
EQ0;
```

MYSQL_FREE_RESULT() This function frees memory used by a query.

```php
int mysql_free_result(int result)
```

Usually you won't need this function, connections to MySQL are automatically closed after a script. If you run some sort of query that returns a few results and the script continues to do some other work, you can clear up the memory used to store the initial query by using mysql_free_result(). This is a good point to note PHP's impressive memory-handling capabilities. When a connection is closed (implicitly at the end of the script or by using mysql_close()) PHP clears all of the memory used by the query. When you are writing applications this is one less thing you will need to worry about.

MYSQL_CLOSE() This closes the link to MySQL.

```php
int mysql_close([int link_identifier])
```

You don't need to use this function, as links opened with mysql_connect are closed automatically at the end of a script's execution, and this has been mentioned.

MYSQL_SEEK() This function repositions the cursor to the row you specify.

```php
int mysql_data_seek(int result, int row)
```

This could be useful if some reason you need to rewind the database.

MYSQL_CREATE() This function creates a table.

```php
int mysql_create(string query)
```
