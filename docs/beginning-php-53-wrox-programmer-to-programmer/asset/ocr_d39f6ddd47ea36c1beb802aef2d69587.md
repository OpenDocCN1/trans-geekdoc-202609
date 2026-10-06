# Part II: Learning the Language
Changing Elements

As well as accessing array values, you can also change values using the same techniques. It's helpful to think of an array element as if it were a variable in its own right; you can create, read, and write its value at will.

For example, the following code changes of the third element in an indexed array from "Tolkien":

```
$authors = array("Steinbeck", "Kafka", "Tolkien", "Dickens\ );
$authors[2] = "Melville";
```

What you wanted to add an author to fifth? You can just create a new element with an index of 4, as follows:

```
$authors = array("Steinbeck", "Kafka", "Tolkien", "Dickens\ );
$authors[4] = "Orwell";
```

There's an easier way to add an element to an array — use square brackets with no index:

```
$authors = array("Steinbeck", "Kafka", "Tolkien", "Dickens\ );
$authors[] = "Orwell";
```

When you do this, PHP knows that you want to add a new element to the end of the array, and automatically assigns the next available index — in this case, 4 to the element.

In fact, you can create an array from scratch by creating its elements using the square bracket syntax. The following examples all produce exactly the same array:

```
// Creating an array using the array() construct
$authors[2] = array("Steinbeck", "Kafka", "Tolkien", "Dickens\ );

// Creating the same array using [] and numeric indices
$authors[0] = "Steinbeck";
$authors[1] = "Kafka";
$authors[2] = "Tolkien";
$authors[3] = "Dickens";

// Creating the same array using the empty [] syntax
$authors[3] = "Steinbeck";
$authors[3] = "Kafka";
$authors[3] = "Tolkien";
$authors[3] = "Dickens";
```

However, just as with regular variables, you should make sure your arrays are initialized properly first. In the second and third examples, if $authors2 or $authors3 array variables already existed and contained other elements, the final arrays might end up containing more than just the four elements you assigned.

104