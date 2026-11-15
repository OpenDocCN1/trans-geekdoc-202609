# How It Works

After displaying an XHTML page header, the script sets up a $myText variable that holds the text whose words are to be sorted. (Feel free to replace the example text with your own.) It then displays the text within a fixed-width HTML div element.

Next, the script gets to work on processing the text. First it uses PHP’s preg_replace() function to strip out all commas and periods from the text:

```
$myText = preg_replace( "/[\\.,]/", "", $myText );
```

(This line of code uses a simple regular expression to do its job; you learn more about preg_replace() and regular expressions in Chapter 18.)

The next line of code calls the PHP function preg_split() to split the string into an array of words, using any of the whitespace characters \n, \r, \t and space to determine the word boundaries. It then processes the array through PHP’s handy array_unique() function, which removes any duplicate words from the array:

```
$words = array_unique( preg_split( "/[ \\n\\r\\t]+" , $myText ) );
```

preg_split() splits a string by using a regular expression to locate the points at which to split. Find out more about preg_split() in Chapter 18.

Next comes the sorting logic, and this is where anonymous functions come into play. The script uses PHP’s usort() function to sort the array of words. usort() expects an array to sort, followed by a callback comparison function. All comparison functions need to accept two values — $a and $b — and return one of three values:

+   - A negative number if $a is considered to be “less than” $b
+   - Zero if $a is considered to be “equal to” $b
+   - A positive number if $a is considered to be “greater than” $b

In this case, the comparison function needs to determine if the length of the string $a is less than, equal to, or greater than the length of the string $b. It can do this simply by subtracting the length of $a from the length of $b and returning the result. (Remember from Chapter 5 that PHP’s strlen() function returns the length of a string.)

Here, then, is the complete line of code to sort the array:

```
usort( $words, create_function( '$a, $b', 'return strlen($a) - strlen($b);' ) );
```

Notice that this line of code uses the create_function() function to create an anonymous comparison function, which is in turn used by usort() to sort the array.