# Part II: Working with PHP

USING WHILE WITH LIST() = EACH()
Another place... often comes into play with arrays, when using the list()
 each() structure. This structure assigns elements in an array to named variables.
It will iterate through the array, and when there are no more elements to pull from,
it will test FALSE, and the loop will stop. When pulling from an array, list()
is expecting an associative array and will take two variables: the first for the key,
second for the value.

```
$knicks = array (center => "Ewing", point => "Childs",
shooting_guard => "Houston",
forward => "Sprewell", strong_forward => "Johnson"
);
echo "<h2>The Knicks 1999 Starting Five Were</h2>";
while (list($key,$value) = each ($knicks))

```

```
echo "$key: $value <br>\n";
```

After running the preceding code array pointer will be at the end of the
if you wish to loop through it again, you will have to move the pointer
to the beginning of the array with reset. In the preceding example, reset
($knicks) would work.

![](bbox=[0.167, 0.447, 0.226, 0.513])

Note that if you don't have an associative array and you wish to grab array values,
y will need to account for it in your list(). Do this by including a comma in
the parentheses.

```
$names = array("John", "Jacob", "Jason", "Josh");
while (list ($value) = each ($names))

```

```
echo "$value <br>\n";
```

If you did not the comma preceding $value, the ordinal placement of each
element would be assigned to value and the code would print "0, 1, 2, 3.\nIf you want to get the keys out of an associative array, your list statement
should contain something like list($key, ).
List is also useful with mysql_fetch_array(). It can be kind of a pain to keep
referring to values by their associative array reference (e.g., $row["first_name").