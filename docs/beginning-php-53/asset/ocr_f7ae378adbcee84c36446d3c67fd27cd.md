However, an element with the same numeric key doesn’t get overwritten; instead the new element is added to the end of the array and given a new index:

```
$authors = array( "Steinbeck", "Kafka", "Tolkien", "Dickens" );
$authors = array_merge( $authors, array( 0 => "Milton" ) );
```

```
// Displays "Array ( [0] => Steinbeck [1] => Kafka [2] => Tolkien [3] => Dickens [4] => Milton )"
print_r ( $authors );
```

If you want to merge arrays while preserving numeric keys, try the array_replace() function (new to PHP 5.3). For details see http://www.php.net/manual/en/function.array-replace.php.

You can also use array_merge() to reindex a single numerically indexed array, simply by passing the array. This is useful if you want to ensure that all the elements of an indexed array are consecutively indexed:

```
$authors = array( 34 => "Steinbeck", 12 => "Kafka", 65 => "Tolkien", 47 => "Dickens" );
```

```
// Displays "Array ( [0] => Steinbeck [1] => Kafka [2] => Tolkien [3] => Dickens )"
print_r( array_merge( $authors ) );
```

# Converting Between Arrays and Strings

PHP provides a few functions that let you convert a string to an array, or an array to a string.

To convert a string to an array, you can use PHP’s handy explode() string function. This function takes a string, splits it into separate chunks based on a specified delimiter string, and returns an array containing the chunks. Here’s an example:

```
$fruitString = "apple,pear,banana,strawberry,peach";
$fruitArray = explode( ",", $fruitString );
```

After running this code, $fruitArray contains an array with five string elements: "apple", "pear", "banana", "strawberry", and "peach".

You can limit the number of elements in the returned array with a third parameter, in which case the last array element contains the whole rest of the string:

```
$fruitString = "apple,pear,banana,strawberry,peach";
$fruitArray = explode( ",", $fruitString, 3 );
```

In this example, $fruitArray contains the elements "apple", "pear", and "banana,strawberry,peach".

Alternatively, specify a negative third parameter to exclude that many components at the end of the string from the array. For example, using –3 in the example just shown creates an array containing just "apple" and "pear". (The three components "banana", "strawberry", and "peach" are ignored.)