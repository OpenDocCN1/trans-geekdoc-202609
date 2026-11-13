use of a function that turns a PHP array (in other words, a list of stuff) into an HTML unordered list (a visible list of stuff).

```
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
```

# ## Returning values

Of course, your functions do more than print HTML. Functions can perform database calls or mathematical computations or do some string handling. They can do just about anything, and often you want to make the rest of the script aware of the results of your function. You can do this by using the keyword return. When a function hits the word return it leaves the function, and it returns whatever value you specify – a variable, a Boolean value (TRUE or FALSE), or nothing at all, if that’s what you prefer. (Note: a plain ‘return;’ statement is equivalent to ‘return NULL;’)

```
```php
function basic_math($val_1, $val_2)
{
	$added = $val_1 + $val_2;
	return $added;
}
```
```

You can then call this function and print the results:

```
```php
$added_value = basic_math(5,4);
echo $added_value;
```
```

If fact, the following works equally well:

```
```php
echo basic_math(5,4);
```
```

Functions can return any variable type (strings, object, arrays, and the like), or, in the case of database calls, they can return result identifiers. Additionally, functions can return FALSE. If you read Chapter 5, you might remember that in PHP any non-zero, non-false value is evaluated in an if statement as TRUE. So you might want to improve the previous function by making sure the values passed can be added.