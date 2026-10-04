# Chapter 7: Writing Organized and Readable Code

```
.<lierrorno=".mysql_errno()>
.<lierror=".mysql_error()>
.<liquery=".$query
;
return $result;
}
```

So your applications might include a file with this function on every page, and then use safe_query() in place of mysql_query().

# Using a variable number of arguments

One nice feature of PHP 4 is that you can pass an indefinite number of arguments to a function and assign the list of arguments to an array. Consider the following code:

> The GLOBALS array is discussed later in this chapter in the "Variable Scope" section.

![](bbox=[0.18, 0.715, 0.253, 0.781])

This function prints out form fields within a table. First, func_get_args() creates an associative array, with the name of the argument as the key. Then each field is printed out. This is pretty convenient because we can call a function in a number of situations and vary the output as many arguments as needed.