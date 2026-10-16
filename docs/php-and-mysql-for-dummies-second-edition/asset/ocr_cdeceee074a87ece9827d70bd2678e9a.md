If the function fails — for instance, if the query is incorrect — `$result` contains `FALSE`.

# ## Getting and using the data

You use the `mysql_fetch_array` function to get the data from the temporary location. The function gets one row of data from the temporary location. The temporary data table might contain only one row of data or, more likely, your select query resulted in more than one row of data in the temporary data table. If you need to fetch more than one row of data from the temporary location, you use the `mysql_fetch_array` function in a loop.

# ### Getting one row of data

To move the data from its temporary location and put it into variables that you can use in your program, you use the PHP function `mysql_fetch_array`. The general format for the `mysql_fetch_array` function is

```
```php
$row = mysql_fetch_array($resultidentifier,typeofarray);
```
```

This statement gets one row from the data table in the temporary location and puts it in an array variable called `$row`. Fill in the following information:

+   - **`resultidentifier`**: The variable that points to the temporary location of the results.
+   - **`typeofarray`**: The type of array that the results are put into. It can be one of two types of arrays or both types. Use one of the following values:
+     - `MYSQL_NUM`: An array with a key/value pair for each column in the row using numbers as keys.
+     - `MYSQL_ASSOC`: An array with a key/value pair for each column in the row using the column names as keys.
+     - `MYSQL_BOTH`: An array with both types of keys. In other words, the array has two key/value pairs for each column: one with a number as the key and one with the column name as the key. If no array type is given in the function call, `MYSQL_BOTH` is assumed.

The `mysql_fetch_array` function gets one row of data from the temporary location. In some cases, one row is all you selected. For instance, to check the password entered by a user, you only need to get the user’s password from the database and compare it with the password that the user entered. The following statements check a password:

```
```php
$userEntry = "secret";    // password user entered in form
$query = "SELECT password FROM Member
          WHERE loginName='qsmith'";
$result = mysql_query($query)
```
```