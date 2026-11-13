Chapter 5 describes the list()=each() construct in more detail. Basically, each() pulls the key and value of a single array element; list() takes those values and assigns them to $key and $value, respectively. This process continues until each element in the array has been accessed. If you want to go through the array a second time, you will need to reset the array pointer with reset($person).

If you wanted to get only the value without the key, or if you were using a non-associative array and wanted to use the list()=each() structure, you would have to do this:

```
while (list( , $value) = each($person))
{
    echo "value = $value<br>\n";
}
```

Or, if you wanted to get at just the keys, you could do this:

```
while (list($key) = each($person))
{
    echo "key = $key<br>\n";
}
```

You can also cycle through arrays using the foreach() loop. The following will print out the keys and values for each element of the $person array:

```
foreach($person as $key=>$value)
{
    echo "key = $key; value = $value<br>\n";
}
```

And the following will print out just the values of array elements:

```
foreach($person as $value)
{
    echo "value = $value<br>\n";
}
```

With foreach() there's no need to reset the array pointer after looping through the array. It is also appreciably faster than the list()=each() syntax.

![](bbox=[0.173, 0.841, 0.253, 0.911])

Think about PHP arrays this way: All arrays are associative. A couple of pages back you saw that you can assign a basic array without specifying associative keys. For example, $myarray= array ("pug", "poodle"). When this is done, PHP assigns $myarray consecutive numeric keys starting at 0.