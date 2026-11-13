# USING while WITH list() = each()

Another place while ... often comes into play is with arrays, when you are using the list() = each() structure. This structure assigns elements in an array to named variables. It will iterate through the array, and when no more elements are left to pull from, it will test false and the while loop will stop. When pulling from an array, list() is expecting an associative array and will take two variables: the first for the key and the second for the value, as illustrated in the following code:

```
```php
$knicks = array (center => "Ewing", point => "Childs",
shooting_guard => "Houston",
forward => "Sprewell", strong_forward => "Johnson"
);
echo "<h2>The Knicks 1999 Starting Five Were</h2>";
while (list($key,$value) = each ($knicks))
{
    echo "$key: $value <br>\n";
}
```
```

> After you run the preceding code the array pointer will be at the end of the array. If you wish to loop through it again, you will have to move the pointer to the beginning of the array with reset. In the preceding example, reset($knicks) would work.

Note that if you don't have an associative array and you wish to grab array values, you will need to account for it in your list(). Do this by including a comma within the list parentheses, as follows:

```
```php
$names = array("John", "Jacob", "Jason", "Josh");
while (list (, $value) = each ($names))
{
    echo "$value <br>\n";
}
```
```

If no comma preceded $value in the preceding code, the ordinal placement of each element would be assigned to $value and the code would print "0, 1, 2, 3".

If you want to get only the keys out of an associative array, your list statement should contain something like list($key, ).

Though we're stressing list's use with the each() statement, it can generally be thought of as an "array destructor," —that is, it pulls elements out of an array. Similarly, each() is an "array iterator," meaning that it walks through all the elements in an array. It doesn't need to be used with list(), though that is by far the most common usage.