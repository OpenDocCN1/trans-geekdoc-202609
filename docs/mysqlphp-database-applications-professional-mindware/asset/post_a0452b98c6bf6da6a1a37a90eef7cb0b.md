
For example, say you had a file that contained a function, but that the function relied on another function from an outside file. You’d do something like this:

```
require 'helpful_file.php';
another_function();
{
    function_from_helpful_file();
}
```

Say we name this file short_function.php. If we needed both short_function.php and helpful_file.php in a third file, we could have a problem. All functions in helpful_file.php would in fact be included twice. If we called one of the twice-included functions, PHP would not be able to resolve the ambiguity and would spit out an error. So in cases like this, use include_once() or require_once(). Note that if files are included more than once we might also have a problem dealing with variables that inadvertently overwrite each other.

Note that include_once() and require_once() inherit behavior from include() and require(): require_once() will only be processed once, and include_once() can be executed multiple times within loops.

## User-Defined Functions

In Chapter 6 you saw many of the functions built into the PHP processing engine. If you are a humble person and look at Appendix E or visit the online PHP manual, you should be duly impressed by the quantity and power of PHP’s built-in functions. But it isn’t enough—and no matter how much work the able developers put into the language, it never will be enough. That is because every developer on the planet has unique needs. We need to accomplish specific tasks, and we need to do it in ways that fit our own styles and predilections.

User-defined functions allow us developers to create blocks of code that achieve specific tasks. The great thing about user-defined functions is that the code becomes reusable. Any piece of code that you find yourself writing over and over should be committed to a function. There’s little doubt that it will save you time in the long run.

![](img/de0823012275cf4ceebdb822a56e6b71_204_0.png)

In the applications presented in this book nearly all of the code is within functions. The files that you see in your browser are very much an assemblage of function calls. As you will see, this helps to keep things readable.

### Function basics

We'll start by writing a simple function that writes out the start of an HTML table.

```
function start_table()
{
    echo "<table border=1>\n";
}
```

To call this function within my PHP page, we would access it just like a built-in PHP function:

```
start_table();
```

That's easy enough. But what if we want the border to vary in given situations? We could make the border a variable, and then in the function call specify the value for border.

```
function start_table($border)
{
    echo "<table border=$border>\n";
}
```

```
start_table(1);
```

Now say that most of the time we want the border to be 1, but would like to be able to change the border within the function call. The following would do the trick:

```
function start_table($border=1)
{
    echo "<table border=$border>\n";
}
```

Here $border has been given a default value of 1. But we can overwrite that value by specifying a different value when calling the function. For example, if we were to call the function with the following command, the table would have a border of 2:

```
start_table(2);
```

Once again, 1 is the default value, so if this function is called with the following code, the table border will be 1:

```
start_table();
```

If you know your HTML, you know that the table tag can have multiple attributes: cellspacing and cellpadding are two others. We could add those to the function, along with default values.

```
function start_table($border=1, $cellspacing=2, $cellpadding=2)
{
echo "<table border=$border cellspacing=$cellspacing
cellpadding=$cellpadding>\n";
}
```

Then, in the call to this function you could alter any of these:

```
start_table(4,2,5);
```

The table created with this command would have a border of 4, cellspacing of 2, and cellpadding of 5.

![](img/de0823012275cf4ceebdb822a56e6b71_206_0.png)

> The values that the function will accept are known as arguments. So the start_table function shown here will take three arguments.

When constructing functions you should be aware that if you wish to change one of the default values in your function call, you must specify all the arguments that precede it (to the left). For instance, the first command in the following code will produce an error. However, the second one will work and will create a table tag with a border of 4, cellspacing of 3, and cellpadding of 2.

```
//this will cause an error
start_table( ,5,5);
//this will work
start_table(4,3);
```

Functions can accept more than simple variables; you can pass any of the scalar types (string, integer, double), any array (numeric, associative, or multi-dimensional), or objects. You might want to make use of a function that turns an array into HTML unordered list, using <ul> and <li>.

```
function create_ul($array)
{
    echo "<ul>\n";
    while(list( , $value) = each ($array))
{
    echo "<li>$value</li>\n";
}
echo "</ul>\n";
}
```

### Returning values

Of course your functions will do more than print HTML. Functions may perform database calls or mathematical computations or do some string handling. They can do just about anything, and often you will want to make the rest of the script aware of the results of your function. You can do this by using the keyword return. When a function hits the word return it leaves the function, and it will return whatever you specify—a variable, a boolean value (TRUE or FALSE), or nothing at all, if that’s what you prefer.

```
function basic_math($val_1, $val_2)
{
    $added = $val_1 + $val_2;
    return $added;
}
```

You could then call this function and print the results.

```
$added_value = basic_math(5,4);
echo $added_value;
```

In fact, the following would work equally well:

```
echo basic_math(5,4);
```

Functions can return any variable type (strings, object, arrays, and the like), or, in the case of database calls, they can return result identifiers. Additionally, functions can return FALSE. If you read Chapter 5, you may remember that in PHP, any non-zero, non-false value will be evaluated in an if statement as true. So we might want to improve the previous function by making sure the values passed can be added.

```
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

If either of the arguments in the call to this function is not an integer, the function will return FALSE and stop. A call to this improved function might look like this.

```
if(!($added_value = basic_math(7, 5)))
{
    echo "What exactly are you doing?";
}
else
{
    echo $added_value;
}
```

If the function returns a value (any value), that value will be added. If not, a special message will be printed. Notice how this mimics the behavior of many of the PHP built-in functions. Its purpose is to perform a task, and if it fails to do so, it returns false.

Actually, there's something else that needs to be pointed out in this function. What will happen if the sum of the arguments sent to the function equal zero, say -1 and 1. In a case like that, your function will return 0. And, as we discussed in Chapter 5, 0 is evaluated as FALSE in PHP. So you need to be careful about situations like this. You may run into situations like this with some of PHP's string handling functions, strpos(), for example. You might be better off evaluating a call to the previous function like this:

```
if (!is_int($added_value = basic_math(-1,1)))
```

Take a quick look at the following function. We think it's a good example of how functions can really save you time, headaches, and keystrokes. The mysql_query function is fine; it sends a query from PHP to MySQL and, if it succeeds, returns a result identifier. If it fails, however, it does not automatically return any error information. Unless you do a bit of digging, you won't know what the problem was with the query. So for every query in your applications (and there will be plenty) you tack on an or die phrase:

```
mysql_query("select * from table_name") or die
("Query failed: " . mysql_error());
```

But life gets quite a bit easier if you create a function like the following, and then send all of your queries through that function.

```
function safe_query ($query = "")
{
    if (empty($query)) { return FALSE; }
    $result = mysql_query($query)
        or die("ack! query failed: "
```
