```
array(3) {
  [1]=>
  string(3) "ABC"
  [2]=>
  string(3) "DEF"
  [3]=>
  string(3) "GHI"
}
```

This tells you that the array has 3 elements. Element [1] is a 3-letter string comprising ABC. Element 2 is a 3-letter string of DEF, and so on.

If this still doesn't help, you can go one step further and output the contents of every variable that the program knows about. Just do this:

```
echo "<pre>";
var_dump(get_defined_vars());
echo "</pre>";
```

This works because there's a PHP function which creates an array containing all of the variables. So we call this function, then use var_dump to display the array. As for the other two lines, the <pre> tag tells the web browser that it's being asked to display preformatted text, and is often used when displaying program listings and the like. Just trust me that the output of var_dump looks much more readable if surrounded by such tags.

While this also produces the list of the contents of the rooms array, it comes at the end of a very long (many hundreds of lines) listing of lots of other variables as well. These are not variables that your program has created, but ones which the web server and PHP use for their own internal purposes. Some of these are very useful. For example, take a look at this extract from the list that is returned on the the-web-book.com server: