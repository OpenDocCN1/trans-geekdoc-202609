There is also a shorthand operator, .=:

```
$a .= $b
```

The above is the equivalent of:

```
$a = $a . $b
```

Remember that if you want to include spaces or new lines between elements of a string, you'll have to do it manually. You can concatenate multiple strings together using the dot operator:

```
$a = "Hello";
$b = "World";
$c = "<b>" . $a . " " . $b . "</b>";
echo($c);
```

# String Functions

PHP offers a wide array of string handling functions. We'll only look at the most commonly used ones here; you can find a complete list of PHP functions in the PHP manual (http://www.php.net/docs.php). We won't cover regular expressions here, but they are by far the most powerful and flexible method of manipulating strings. These are covered in depth in Chapter 7.

# substr()

```
string substr(string string, int start [, int length])
```

The substr() function returns a section of the string. The first argument is the complete string, the second is the position within the string of the first character you want to be returned (counting from zero), while the third is the position of the last character of the string that you want to return. If you don't specify the third argument, then PHP will assume that you just wanted to include the rest of the string. Here are some examples of substr() in action:

```
$String1 = substr("The cat sat on the mat", 4,3); // 'cat'
$String2 = substr("The frog sat on the log", 0,1); // 'T'
$String3 = substr("The aardvark sat in the dark", 17); // 'in the dark'
```

# strpos()

```
int strpos(string haystack, string needle [, int offset])
```

strpos() provides the opposite functionality to the substr() function. You supply it with a subsection of a string and it returns the first place within the string that the subsection can be found (if it can be found at all).

You supply the string you wish to search first, the string you are hoping to find as the second argument, and lastly there is an optional argument which allows you to specify a position within the string to start looking from. Some examples of strpos():