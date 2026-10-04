# Part II: Working with PHP

```
while($row = mysql_fetch_array($result))
{
  //process row
}
```

Finally, there are occasions where a function will return nothing. This will be common in functions that perform a specific action, like closing a connection to the database or the file system.

# Function Documentation

As we have repeatedly throughout this book, the PHP online manual is your friend. The documentation team is amazing, and we really believe the quality of the online manual is one of the reasons for the success of the language. As there is no way we can cover every PHP function in this book, you will need to consult the manual. For that reason, we will want to take a minute to go over the functions we are presented in the manual.
A typical manual reference will look like this:

```
int mysql_affected_rows ([int link_identifier])
```

This function returns the number of rows affected by an update, insert, or delete query. Looking at it, you will see that the first (int) indicates the variable type that will be returned. This could be any of the variable types or void (meaning the function will return nothing). Then within the parameters there will be a list of arguments. The type of argument is listed as well as what it represents. Note that optional arguments are placed in brackets. So above, the function requires no arguments but one: connection identifier grabbed from mysql_connect(). In a case like phpinfo(), you will see that the argument list is void.
In the preceding example, if you pass an argument, it it better to be an integer. If you were to give it a string or an array, you will get an error.

# Important PHP 4 Functions

In this section, we will attempt to break down PHP 4 functions into logical groupings. Along the way we will cover every function used in the applications presented in this book.