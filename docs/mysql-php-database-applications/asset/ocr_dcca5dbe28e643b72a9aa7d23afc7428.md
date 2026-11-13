```
".<li>error=".mysql_error()
".<li>query=".$query
);
return $result;
}
```

So your applications might include a file with this function on every page, and then you can use `safe_query()` in place of `mysql_query()`.

# Using a variable number of arguments

One nice feature of PHP is that you can pass an indefinite number of arguments to a function and then assign the list of arguments to an array. Consider the following code:

```
function print_input_fields()
{
    $fields = func_get_args();
    foreach ($fields as $field)
    {
        if (isset($GLOBALS[$field]))
        {
            $value = $GLOBALS[$field];
        }
        else
        {
            $value = '';
        }
        print " <tr>\n";
        print " <td valign=top
        align=right><b>".ucfirst($field).":</b></td>\n";
        print " <td valign=top align=left><input type=text
        name=$field size=40 value=\"$value\"/></td>\n";
        print " </tr>\n\n";
    }
}
start_table();
print_input_fields("name","location","email","url");
end_table();
```

![](bbox=[0.1, 0.86, 0.19, 0.92])

The $GLOBALS array is discussed later in this chapter in the “Variable scope” section.