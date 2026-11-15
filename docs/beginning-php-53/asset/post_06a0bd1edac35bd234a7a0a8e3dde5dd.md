
<body>
<h1>Using each() with a while loop</h1>
<dl>
<?php
$myBook = array( "title" => "The Grapes of Wrath",
"author" => "John Steinbeck",
"pubYear" => 1939 );
while ( $element = each( $myBook ) ) {
echo "<dt>$element[0]</dt>";
echo "<dd>$element[1]</dd>";
}
?>
</dl>
</body>
</html>
```

![](img/1ddec54918a4802eb9b4febec3d4e7f6_150_0.png)

Figure 6-3

The while loop continues as long as each() keeps returning a four-element array (which evaluates to true). When the end of the array is reached, each() returns false and the loop finishes.

## Looping Through Arrays with foreach

As you just saw, it’s easy to use each() in combination with while to loop through all the elements of an array. In fact, there’s an even easier way: you can use PHP’s foreach statement.

foreach is a special kind of looping statement that works only on arrays (and objects). You can use it in two ways. You can either retrieve just the value of each element, or you can retrieve the element's key and value.

### Using foreach to Loop Through Values

The simplest way to use foreach is to retrieve each element's value, as follows:

```
foreach ( $array as $value ) {
    // (do something with $value here)
}

// (rest of script here)
```

As you might imagine, the foreach loop continues to iterate until it has retrieved all the values in the array, from the first element to the last. On each pass through the loop, the $value variable gets set to the value of the current element. You can then do whatever you need to do with the value within the loop's code block. Then, the loop repeats again, getting the next value in the array, and so on.

Here's an example:

```
$authors = array( "Steinbeck", "Kafka", "Tolkien", "Dickens" );

foreach ( $authors as $val ) {
    echo $val . "<br/>";
}
```

This code displays:

```
Steinbeck
Kafka
Tolkien
Dickens
```

Note that you can use any variable name you like to store the value. Essentially, any variable that you place after the as in the foreach statement gets assigned the current element's value.

### Using foreach to Loop Through Keys and Values

To use foreach to retrieve both keys and values, use the following syntax:

```
foreach ( $array as $key => $value ) {
    // (do something with $key and/or $value here
}

// (rest of script here)
```

This behaves exactly like the previous foreach construct; the only difference is that the element's key is also stored in the $key variable. (Again, you can use any variable names you like; they don't have to be $key and $value.)

Now you can rewrite the example that used `each()` with a `while` loop in the previous section ("Stepping Through an Array") to use a `foreach` loop instead:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Using foreach</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Using foreach</h1>

<dl>

<?php
$myBook = array( "title" => "The Grapes of Wrath",
"author" => "John Steinbeck",
"pubYear" => 1939 );

foreach ( $myBook as $key => $value ) {
echo "<dt>$key</dt>";
echo "<dd>$value</dd>";
}
?>

</dl>
</body>
</html>
```

This code produces the same list of keys and values as shown in Figure 6-3.

## Altering Array Values with foreach

When using `foreach`, the values you work with inside the loop are copies of the values in the array itself. This means that if you change the value given to you by `foreach`, you're not affecting the corresponding value in the original array. The following example code illustrates this:

```
$authors = array( "Steinbeck", "Kafka", "Tolkien", "Dickens" );

// Displays "Steinbeck Kafka Hardy Dickens";
foreach ( $authors as $val ) {
if ( $val == "Tolkien" ) $val = "Hardy";
echo $val . " ";
}

echo "<br>";

// Displays "Array ( [0] => Steinbeck [1] => Kafka [2] => Tolkien [3] => Dickens )"
print_r ( $authors );
```

Notice that, although `$val` was changed from "Tolkien" to "Hardy" within the loop, the original `$authors` array remains untouched, as evidenced by the output from `print_r()` on the final line.

However, if you do want to modify the array values themselves, you can get `foreach()` to return a reference to the value in the array, rather than a copy. This means that the variable within the loop points to the value in the original array element, allowing you to change the element's value simply by changing the variable's value.

To work with references to the array elements rather than copies of the values, simply add a & (ampersand) symbol before the variable name within the `foreach` statement:

```
foreach ( $array as &$value ) {
```

Here's the previous example rewritten to use references:

```
$authors = array( "Steinbeck", "Kafka", "Tolkien", "Dickens" );
// Displays "Steinbeck Kafka Hardy Dickens";
foreach ( $authors as &$val ) {
    if ( $val == "Tolkien" ) $val = "Hardy";
    echo $val . " ";
}
```

```
unset( $val );
echo "<br/>";
```

```
// Displays "Array ( [0] => Steinbeck [1] => Kafka [2] => Hardy [3] => Dickens )"
print_r ( $authors );
```

Notice how, this time, the third element's value in the `$authors` array is changed from "Tolkien" to "Hardy" in the array itself.

By the way, the `unset( $val )` line ensures that the `$val` variable is deleted after the loop has finished. This is generally a good idea, because when the loop finishes, `$val` still holds a reference to the last element (that is, "Dickens"). If you were to change `$val` later in your code, you would inadvertently alter the last element of the `$authors` array. By `unsetting` (deleting) `$val`, you safeguard against this potential bug.

References are a powerful tool, and they're explained in more detail in the next chapter.

## Working with Multidimensional Arrays

So far, all the arrays you've worked with in this chapter have contained simple values, such as strings and integers. However, arrays can get a lot more powerful than this. As mentioned in "The Anatomy of an Array," earlier in this chapter, PHP arrays can store values of any type. This includes resources, objects, and, more importantly, other arrays.

This ability of arrays to store other arrays in their elements allows you to create multidimensional arrays (also known as nested arrays because they comprise one or more arrays nested inside another). An array that contains other arrays is a two-dimensional array. If those arrays also contain arrays, then the top-level array is a three-dimensional array, and so on.

## Creating a Multidimensional Array

The following script creates a simple two-dimensional array called $myBooks, then displays its contents using print_r(). You can see the result in Figure 6-4.

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>A Two-Dimensional Array</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>A Two-Dimensional Array</h1>

<?php

$myBooks = array(
    array(
        "title" => "The Grapes of Wrath",
        "author" => "John Steinbeck",
        "pubYear" => 1939
    ),
    array(
        "title" => "The Trial",
        "author" => "Franz Kafka",
        "pubYear" => 1925
    ),
    array(
        "title" => "The Hobbit",
        "author" => "J. R. R. Tolkien",
        "pubYear" => 1937
    ),
    array(
        "title" => "A Tale of Two Cities",
        "author" => "Charles Dickens",
        "pubYear" => 1859
    ),
);

echo "<pre>";
print_r ( $myBooks );
echo "</pre>";

?>

</body>
</html>
```

![](img/1ddec54918a4802eb9b4febec3d4e7f6_155_0.png)

Figure 6-4

As you can see, this script creates an indexed array, $myBooks, that contains four elements with the keys 0, 1, 2, and 3. Each element is, in turn, an associative array that contains three elements with keys of "title", "author", and "pubYear".

Although this array is a simple example, it gives you some idea of the power of multidimensional arrays. You could potentially store thousands and thousands of books in this array, with as much information as you like about each book.

## Accessing Elements of Multidimensional Arrays

Using the square bracket syntax that you've already learned, you can access any element within a multidimensional array. Here are some examples (these work on the $myBooks array just shown):

```
// Displays "Array ( [title] => The Trial [author] => Franz Kafka [pubYear] => 1925 ) ";
print_r( $myBooks[1] );
```

```
// Displays "The Trial"
echo "<br/>". $myBooks[1]["title"]. "<br/> ";
```

```
// Displays "1859"
echo $myBooks[3]["pubYear"]. "<br/> ";
```
