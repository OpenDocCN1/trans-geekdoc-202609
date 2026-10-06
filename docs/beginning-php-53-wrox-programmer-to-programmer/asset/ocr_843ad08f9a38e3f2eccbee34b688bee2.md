# Part II: Learning the Language

This code removes all the elements from the second position in the array (position 1) to the end
of the array.

Finally, the fourth example demonstrates that you do not have to pass an array as the fourth argument.
If you have only one element to add — a string value — you can just pass the value. This is
because array_splice() automatically casts the fourth argument to an array before using it. So the
string "Orwell" gets converted into an array with a single element ("Orwell") before being added to
the array.

```
print_r( array_splice($authors, 1, 0, "orwell\ ));
```

By the way, you will have noticed that the script outputs a lot of the more repetitive by creating
variables to store snippets of markup ($Headingstart, HeadingEnd, RowStart,
$nextCell, $rowEnd). Not only does this make the PHP code more compact and easier to follow,
but it makes it easier to change the markup at a later point if needed.

Note that, when inserting an array, the keys of the inserted elements are not preserved; they're
reindexed using numeric keys. array_splice() is not useful for inserting associative arrays.
For example:

```
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

Notice how the "Milton" element has its original key ("authorName") replaced with a numeric
key (1).

# Merging Arrays Together

If you want to join two or more arrays to produce one big array, you need the array_merge()
function. This function takes one or more arrays as arguments, and returns the merged array. (The
original array(s) are not affected.)