Core PHP Programming

```
//move internal pointer
next($colors);

//set internal pointer to first element
reset($colors);

//show which element we're at (red)
print(current($colors));
?
```

# rsort(array unsorted_array)

The rsort function sorts an array in reverse order. With other sorting functions, the presence of being string values will cause all elements to be treated as strings and will be sorted alphabetically. If all the elements are numbers, they will be sorted numerically. The difference between rsort and asort is that rsort discards any key and reigns elements with key values starting at zero. Chapter 15 discusses sorting in depth.

```
?//create test data
$colors = array("one"->"orange", "two"->"cyan", "three"->"purple");

//sort and discard keys
rsort($colors);

//show array
foreach($colors as $key->$value)
{
    print("$key = $value<BR>\n");
}
?
```

# shuffle(array data)

The shuffle function randomly rearranges the elements in an array. The srand function may be used to seed the random number generator, but as with the rand function, a seed based on the current time will be used if you do not provide a seed.

```
?//create test data
$numbers = range(1, 10);

//rearrange
shuffle($numbers);
```

IT-SC book 240