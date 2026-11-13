
use of a function that turns a PHP array (in other words, a list of stuff) into an HTML unordered list (a visible list of stuff).

```php
function create_ul($array)
{
    echo "<ul>\n";
    foreach ($array as $value)
    {
        echo "<li>$value</li>\n";
    }
    echo "</ul>\n";
}
```

## Returning values

Of course, your functions do more than print HTML. Functions can perform database calls or mathematical computations or do some string handling. They can do just about anything, and often you want to make the rest of the script aware of the results of your function. You can do this by using the keyword return. When a function hits the word return it leaves the function, and it returns whatever value you specify – a variable, a Boolean value (TRUE or FALSE), or nothing at all, if that’s what you prefer. (Note: a plain ‘return;’ statement is equivalent to ‘return NULL;’)

```php
function basic_math($val_1, $val_2)
{
    $added = $val_1 + $val_2;
    return $added;
}
```

You can then call this function and print the results:

```php
$added_value = basic_math(5,4);
echo $added_value;
```

In fact, the following works equally well:

```php
echo basic_math(5,4);
```

Functions can return any variable type (strings, object, arrays, and the like), or, in the case of database calls, they can return result identifiers. Additionally, functions can return FALSE. If you read Chapter 5, you might remember that in PHP any non-zero, non-false value is evaluated in an if statement as TRUE. So you might want to improve the previous function by making sure the values passed can be added.

```php
function basic_math($val_1, $val_2)
{
    if (!is_int($val_1) || !is_int($val_2))
    {
        return FALSE;
    }

    $added = $val_1 + $val_2;
    return $added;
}
```

If either of the arguments in the call to this function is not an integer, the function returns FALSE and stops. A call to this improved function might look like this:

```php
if (($added_value = basic_math(7, 5)) == FALSE)
{
    echo "What exactly are you doing?";
}
else
{
    echo $added_value;
}
```

If the function returns a value (any value), that value is added. If not, a special message is printed. Notice how this mimics the behavior of many of the PHP built-in functions. Its purpose is to perform a task, and if it fails to do so, it returns FALSE.

Take a quick look at the following function. It’s a good example of how functions can really save you time, headaches, and keystrokes. The mysql_query function is fine; it sends a query from PHP to MySQL and, if it succeeds, returns a result identifier. If it fails, however, it does not automatically return any error information. Unless you do a bit of digging, you won’t know what the problem was with the query. So for every query in your applications (and there will be plenty), you tack on an or die phrase:

```php
mysql_query("select * from table_name") or die
("Query failed: " . mysql_error());
```

But life gets quite a bit easier if you create a function like the following and then send all of your queries through that function:

```php
function safe_query ($query = "")
{
    if (empty($query)) { return FALSE; }
    $result = mysql_query($query)
    or die("ack! query failed: "
    ."<li>errno=".mysql_errno()
    ."<li>error=".mysql_error()
    ."<li>query=".$query
    );
    return $result;
}
```

So your applications might include a file with this function on every page, and then you can use `safe_query()` in place of `mysql_query()`.

## Using a variable number of arguments

One nice feature of PHP is that you can pass an indefinite number of arguments to a function and then assign the list of arguments to an array. Consider the following code:

```php
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

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_250_0.png)

The $GLOBALS array is discussed later in this chapter in the “Variable scope” section.

This function prints out form fields within a table. First, func_get_args() creates an associative array, with the name of the argument as the key. Then each form field is printed out. This strategy is pretty convenient because you can call a function in a number of situations and vary the output by including as many arguments as needed.

If you're wondering how this might work if your function contains some required parameters prior to the set of arguments that might vary, good for you. That's an excellent question.

Two other PHP functions work in such situations: func_num_args(), which returns the number of arguments sent to a function, and func_get_arg(), which returns a specific argument based on its numeric index, starting at 0. So, for example, you might have a function that prints an HTML form with a variable number of input fields, like the following:

```php
function print_form($action="", $method="POST")
{
    if (empty($action)) { return FALSE; }
    echo "<form action=$action method=$method>";
    $numargs = func_num_args();
    for ($i = 2; $i < $numargs; $i++)
    {
        echo "<input type=text name=" . func_get_arg($i) . ">";
    }
    echo "</form>";
}

print_form("myurl1.php", "", "myfield1", "myfields2");
```

Be aware that empty() might behave differently than you expect. It returns true if the evaluated variable is not defined, or if it contains "", 0, "0", NULL, FALSE, or an array with no elements.

## Variable scope

To work with functions you need to understand how PHP handles variable scope. Scope is an important topic in any programming language, and PHP is no different.

In PHP, variables assigned outside of functions are known as global variables. These can be variables that you create, they can come from HTML form elements through either GET or POST, or they can be any of the variables inherited from the Apache environment. All globals are accessible from an array known as $GLOBALS. You can add to and delete from this array.

We've said it before, and we'll say it again: Use phpinfo() to get information about variables in your environment or your configuration.

In PHP a global variable is not automatically available within a function. If you want to use a global within a function you must indicate within the function that the variable you are accessing is a global.

Here is an example of using a global within a function:

```php
function add_numbers($val_2)
{
     global $number;
     echo $number + $val_2;
}

$number = 10;
add_numbers(5);
```

This code prints 15. Here $number is a global because it is assigned outside of a function. Using the keyword global tells PHP that you want to fetch the specified number from the $GLOBALS array. The preceding code can also be written like this:

```php
function add_numbers($val_2)
{
     echo $GLOBALS["number"] + $val_2;
}

$number = 10;
add_numbers(5);
```

In the applications in this book we use the technique shown in the first example because it seems a little cleaner, and because directly manipulating the $GLOBALS array is not really encouraged. It's nice to see where your variable is coming from at the top of the function.

Within your functions, you might want to make variables available as globals. That way they are available in the body of your script and in other functions. You can create a global variable the same way you access a previously defined one, with the global keyword. Here's a quick example:

```php
function assign_to_global($val_1, $val_2)
{
     global $sum;
```
