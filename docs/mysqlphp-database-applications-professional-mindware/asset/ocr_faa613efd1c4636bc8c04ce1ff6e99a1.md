```
."><li>errorno=".mysql_errno()
."><li>error=".mysql_error()
."><li>query=".$query
);
    return $result;
}
```

So your applications might include a file with this function on every page, and then use safe_query() in place of mysql_query().

# Using a variable number of arguments

One nice feature of PHP 4 is that you can pass an indefinite number of arguments to a function and then assign the list of arguments to an array. Consider the following code:

```
function print_input_fields()
{
    $fields = func_get_args();
    while (list($index,$field) = each($fields))
    {
        print " <tr>\n";
        print " <td valign=top align=right><b>".ucfirst($field).":</b></td>\n";
        print " <td valign=top align=left><input type=text name=$field size=40 value=\"". $GLOBALS[$field]."\"></td>\n";
        print " </tr>\n\n";
    }
}
start_table();
print_input_fields("name","location","email","url");
end_table();
```

![](bbox=[0.18, 0.7, 0.25, 0.77])

> The GLOBALS array is discussed later in this chapter in the “Variable Scope” section.

This function prints out form fields within a table. First, using func_get_args() creates an associative array, with the name of the argument as the key. Then each form field is printed out. This is pretty convenient because we can call a function in a number of situations and vary the output by including as many arguments as needed.