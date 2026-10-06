
# Part II: Learning the Language

```php
print_r( $authors );
echo $nextCell;
print_r( array_splice( $authors, 2, 0, $arrayToAdd ));
echo $nextCell;
print_r( $arrayToArray );
echo $nextCell;
print_r( $authors );
echo $rowEnd;
echo "${($headingStart)2. Replacing two elements with a new element${($headingEnd)}"

$authors = array( "Steinbeck", "Kafka", "Tolkien" );
$arrayToAdd = array( "Bronte" );
echo $rowStart;
print_r( $authors );
echo $nextCell;
print_r( array_splice( $authors, 0, 2, $arrayToAdd ) );
echo $nextCell;
print_r( $arrayToAdd );
echo $nextCell;
print_r( $authors );
echo $rowEnd;

echo "${($headingStart)3. Removing the last two elements${($headingEnd)}"

$authors = array( "Steinbeck", "Kafka", "Tolkien" );
echo $rowStart;
print_r( $authors );
echo $nextCell;
print_r( array_splice( $authors, 1 ) );
echo $nextCell;
echo "Nothing";
echo $nextCell;
print_r( $authors );
echo $rowEnd;

echo "${($headingStart)4. Inserting a string instead of an array${($headingEnd)}"

$authors = array( "Steinbeck", "Kafka", "Tolkien" );
echo $rowStart;
print_r( $authors );
echo $nextCell;
print_r( array_splice( $authors, 1, 0, "Orwell" ) );
echo $nextCell;
echo "Orwell";
echo $nextCell;
print_r( $authors );
echo $rowEnd;

echo '</table>';

?>

<body>
</html>
```

## Chapter 6: Arrays

![](img/ede05b7b77968b82cbd9a513122fb183_170_0.png)

| Original array | Removed | New array |
| --- | --- | --- |
| [0] => Steinbeck | [0] => Melville | [0] => Steinbeck |
| [1] => Kafka | [1] => Hardy | [1] => Kafka |
| [2] => Tolkien | | [2] => Tolkien |

## 2. Replacing elements with a new element

| Original array | Removed | New array |
| --- | --- | --- |
| [0] => Steinbeck | [0] => Steinbeck | [0] => Bronte |
| [1] => Kafka | | [1] => Kafka |
| [2] => Tolkien | | [2] => Tolkien |

## 3. Removing the last two elements

| Original array | Removed | New array |
| --- | --- | --- |
| [0] => Steinbeck | [0] => Kafka | [0] => Steinbeck |
| [1] => Kafka | [1] => Tolkien |

## 4. Inserting a string instead of array

| Original array | Removed | New array |
| --- | --- | --- |
| [0] => Steinbeck | | [0] => Steinbeck |
| [1] => Kafka | | [1] => Orwell |
| [2] => Tolkien | | [2] => Kafka |
| | | [3] => Tolkien |

Done:

## How It Works

This script demonstrates four different uses of array_splice(), displaying the results in an HTML table. The first example inserts two elements at the third position in the array, displaying the removed elements, which in this case is an empty array because no elements were removed:

```php
array_splice( $authors, 2, 0, $arrayToAdd );
```

You can read this as: "At the third position (2), remove (0) elements, then insert $arrayToArray."

The second example demonstrates how to remove and insert elements at the same time:

```php
array_splice($authors, 0, 2, $arrayToAdd );
```

This code removes two elements from the start of the array (position 0), and inserts the contents of $arrayToArray at position 0.

The third example shows what happens if you omit the third argument:

```php
array_splice($authors, 1 );
```

This code removes all the elements from the second position (position 1) to the end of the array.

Finally, the fourth example demonstrates that you do not have to pass an array as the fourth argument. If you have only one element to add — a string value — you can just pass the value. This is because array_splice() automatically casts the fourth argument to an array before using it. So the string "Orwell" gets converted into an array with a single element ("Orwell") before being added to the array.

```php
array_splice($authors, 1, 0, "Orwell");
```

By the way, you will have noticed that the script outputs a lot of repetitive by creating variables to store snippets of markup. Not only does this make the PHP code more compact and easier to follow, but it makes it easier to change the markup at a later point if needed. Note that, when inserting an array, the keys of the inserted elements are not preserved; they are reindexed using numeric keys. array_splice() is not useful for associative arrays. For example:

```php
$authors = array("Steinbeck", "Kafka", "Tolkien");
array_splice($authors, 1, 0, array("authorName" => "Milton"));
echo "<pre>";
print_r($authors);
echo "</pre>";
```

This code produces the following result:

```
Array
{
[0] => Steinbeck
[1] => Milton
[2] => Kafka
[3] => Tolkien
}
```

Notice how the "Milton" element has its original key ("authorName") replaced with a numeric key (1).

## Merging Arrays

If you want to join two or more arrays to produce one big array, you need the array_merge() function. This function takes one or more arrays as arguments, and returns the merged array (the original array(s) are not affected.) Here's an example:

```php
$authors = array("Steinbeck", "Kafka");
$moreAuthors = array("Tolkien", "Milton");
print_r(array_merge($authors, $moreAuthors));
```

Note that array_merge() joins the elements of arrays to produce the final array. It contrasts with array_push(), array_shift(), and the square bracket syntax, which insert to produce multiple arrays.

```php
$authors = array("Steinbeck", "Kafka");
$moreAuthors = array("Tolkien", "Milton");
array_push($authors, $moreAuthors);
print_r($authors);
```

This produces: Array ([0] => Steinbeck, [1] => Kafka, [2] => Array ([0] => Tolkien ...)).

A feature of array_merge() is that it preserves the keys of associative arrays, so you can use it to add new key/value pairs to an associative array:

```php
$myBook = array("title" => "Grapes of Wrath", "author" => "John Steinbeck", "pubYear" => 1939);
$myBook = array_merge($myBook, array("numPages" => 464));
```

This produces: Array ([title] => Grapes of Wrath, [author] => John Steinbeck, [numPages] => 464).

If you add a key/value using a string that already exists in the array, the original element gets overwritten. This makes array_merge() handle for updating associative arrays:

```php
$myBook = array("title" => "Grapes of Wrath", "author" => "John Steinbeck", "pubYear" => 1939);
$myBook = array_merge($myBook, array("title" => "East of Eden", "pubYear" => 1952));
```

This produces: Array ([title] => East of Eden, [author] => John Steinbeck, [pubYear] => 1952).

However, an element with the same numeric key doesn't get overwritten; instead the new element is added to the array and given a new index:

```php
$authors = array("Steinbeck", "Kafka", "Tolkien", "Dickens");
$authors = array_merge($authors, array(0 => "Milton"));
```

This displays: Array ([0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Dickens, [4] => "Milton"). print_r($authors);

If you want to merge arrays while preserving numeric keys, the array_replace() function (new to PHP 5.3). For details http://www.php.net/manual/en/function.array-replace.php.

You can use array_merge() to reindex a numerically indexed array, simply by passing the array. This is useful to ensure that all the elements of an array are correctly indexed:

```php
$authors = array(34 => "Steinbeck", 12 => "Kafka", 65 => "Tolkien", 47 => "Dickens");
```

This displays: Array ([0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Dickens). print_r(array_merge($authors));

## Converting Arrays and Strings

PHP provides a few functions that can convert a string to an array, or an array to a string.

To convert a string to an array, you can use PHP's explode() string function. This function takes a string, splits it into separate chunks based on a specified delimiter, and returns an array containing the chunks. Here's an example:

```php
$fruitString = "apple,pear,banana,strawberry,peach";
$fruitArray = explode(",", $fruitString);
```

After this code, $fruitArray contains an array with five elements: "apple", "pear", "banana", "strawberry", and "peach".

You can limit the number of elements in the returned array with a third parameter, in which case the array element contains the whole rest of the string:

```php
$fruitString = "apple,pear,banana,strawberry,peach";
$fruitArray = explode(",", $fruitString, 3);
```

In this example, $fruitArray contains the elements "apple", "pear", and "banana", "strawberry", "peach".

Alternatively, specify a negative parameter to exclude that many components at the end of the string from the array. For example, using -3 in the example just creates an array containing just "apple" and "pear". (The three components "banana", "strawberry", and "peach" are ignored).
