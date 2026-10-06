
## Chapter 6: Arrays

Now you can rewrite the example that used each() with a while loop in the previous section ("Stepping Through an Array") to use a foreach loop instead:

```php
<!DOCTYPE html PUBLIC "//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/DTD/xhtml-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Using foreach</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Using foreach</h1>h>
<dl>

<?php
$MyBook = array("title" => "The Grapes of Wrath",
"author" => "John Steinbeck",
"pubYear" => 1939 );

foreach ($MyBook as $key => $value) {
echo "<dt>$key</dt>";
echo "<dd>$value</dd>";
}
?>

</dl>
</body>
</html>
```

This code produces the main list of keys and values as shown in Figure 6-3.

## Altering Array Values with foreach

When using foreach, the values you work inside the loop are copies of the values in the array itself. If it means that you change the value given to you by foreach, you are not affecting the corresponding value in the original array. The following example illustrates this:

```php
$authors = array("Steinbeck", "Kafka", "Tolkien", "Dickens");

// Displays Steinbeck Kafka Hardy Dickens:
foreach ($authors as $val) {
  if ($val == "Tolkien") $val = "Hardy";
  echo $val . " ";
}
echo "<br/>";

// Displays Array ( [0] => Steinbeck [1] => Kafka [2] => Tolkien [3] => Dickens )
print_r ($authors);
```

Notice that, although $val was changed from 'Tolkien' to 'Hardy' within the loop, the original $authors array remains untouched, as evidenced by the output from print_r() on the final line.

However, if you want to modify the array values themselves, you can get foreach() to return a reference to the value in the array, rather than a copy. This means the variable in the loop points to the value in the original array element, allowing you to change the element's value simply by changing the variable's value.

To work with the array elements rather than copies of the values, simply add a & (ampersand) symbol before the variable within the foreach statement:

```php
foreach ($authors as &$val) {
```

Here is the previous example rewritten to use references:

```php
$authors = array( "Steinbeck", "Kafka", "Tolkien", "Dickens" );

// Displays Steinbeck Kafka Hardy Dickens;
foreach ($authors as &$val) {
  if ($val == "Tolkien") $val = "Hardy";
  echo $val . " ";
}

unset($val);
echo "<br/>";

// Displays Array ( [0] => Steinbeck [1] => Kafka [2] => Hardy [3] => Dickens )
print_r( $authors );
```

Notice how, this time, the element's value in the $authors array is changed from "Tolkien" to "Hardy" in the array itself.

By the way, unset($val) line ensures that the $val variable is deleted after the loop has finished. This is generally a good idea, because when the loop finishes, $val still holds a reference to the element (that is, "Dickens"). If you were to change $val in your code, you would inadvertently alter the last element of the $authors array. By unsetting($val), you safeguard against this potential bug.

References are a powerful tool, and they're explained in more detail in the next chapter.

## Working with Multidimensional Arrays

So all, the arrays you worked with in this chapter have contained simple values, as strings and integers. However, arrays can get lot more powerful than this. As mentioned in "The Anatomy of an Array," earlier in this chapter, PHP arrays can store values of any type. This includes resources, objects, and more importantly, other arrays.

This ability of arrays to store other arrays in their elements allows you to create multidimensional arrays (also known as nested arrays because they comprise one or more arrays nested inside another). An array that contains other arrays is a two-dimensional array. If those arrays also contain arrays, the top-level array is a three-dimensional array, and so on.

## Creating a Multidimensional Array

The following script creates a simple multidimensional array called $myBooks, displays its contents using print_r(). You can see the result in Figure 6-4.

```php
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" lang="en">
<head>
  <title>A Two-Dimensional Array</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
  <h1>A Two-Dimensional Array</h1>

<?php
$myBooks = array(
  "title" => "The Grapes of Wrath"
```

![](img/ede05b7b77968b82cbd9a513122fb183_155_0.png)

## A Two-Dimensional Array

Array
[0] => Array
{
  [title] => The Grapes of Wrath
  [author] => John Steinbeck
  [pubYear] => 1939
}
[1] => Array
{
  [title] => The Trial
  [author] => Franz Kafka
  [pubYear] => 1925
}
[2] => Array
{
  [title] => The Hobbit
  [author] => J. R. R. Tolkien
  [pubYear] => 1937
}
[3] => Array
{
  [title] => A Tale of Two Cities
  [author] => Charles Dickens
  [pubYear] => 1859
}

## Accessing Elements of Multidimensional Arrays

You know how to use foreach for simple arrays, but how do you loop through multidimensional arrays? Well, because multidimensional arrays are nested inside others, you can use nested foreach loops. This example shows how.

## Displaying an Array

The following script uses nested foreach loops to show you how to loop through a multidimensional array. Save it as multidimensional_loop.php within your document folder, then browse to its URL to see something like Figure 6-5.

```php
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" lang="en">
<head>
  <title>Looping Through Two-Dimensional Array</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
  <h1>Looping Through Two-Dimensional Array</h1>

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
  )
);
$bookNum = 0;

foreach ($myBooks as $book ) {
  $bookNum++;
  echo "<h2>Book $bookNum:</h2>h";
  echo "<dl>";

  foreach ($book as $key => $value ) {
    echo "<dt>$key</dt><dd>$value</dd>";
  }

  echo "</dl>";
}
?>
</body>
</html>
```

![](img/ede05b7b77968b82cbd9a513122fb183_157_0.png)
