```
while($row = mysql_fetch_array($result))
{
    //process row
}
```

Finally, there are occasions where a function will return nothing. This will be common in functions that perform a specific action, like closing a connection to a database or the file system.

# Function Documentation

As we say repeatedly throughout this book, the PHP online manual is your friend. The documentation team is amazing, and we really believe the quality of the online manual is one of the reasons for the success of the language. As there is no way we can cover every PHP function in this book, you will need to consult the manual. For that reason, we want to take a minute to go over how the functions are presented in the manual.

A typical manual reference will look something like this:

```
int mysql_affected_rows ([int link_identifier])
```

This function returns the number of rows affected by an update, insert, or delete query. Looking at this, you can see that the first portion (int) indicates the variable type that will be returned. This could be any of the variable types or void (meaning that the function will return nothing). Then within the parentheses there will be a list of arguments. The type of argument is listed as well as what it represents. Note that optional arguments are placed in brackets. So above, the function requires no arguments but has one optional argument: the connection identifier grabbed from mysql_connect(). In a case like phpinfo(), you will see that the argument list is void.

In the preceding example, if you pass an argument, it better be an integer. If you were to give it a string or an array, you will get an error.

# Important PHP 4 Functions

In this section, we will attempt to break down PHP 4 functions into logical groupings. Along the way we will cover every function used in the applications presented in this book.