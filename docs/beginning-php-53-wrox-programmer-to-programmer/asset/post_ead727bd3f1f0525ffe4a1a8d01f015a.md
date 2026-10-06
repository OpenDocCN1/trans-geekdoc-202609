
# Exercises

- 1. Using the `printf()` function, write a single line of code that takes a month (from 1 to 12), a day (from 1 to 31), and a four-digit year, and displays the resulting date, formatted in mm/dd/yyyy format. Don't forget to add a zero in front of the month or day if it's less than 10.

- 2. Write a script that emulates the function call `str_pad($myString, $desiredLength)`. In other words, take a string, and add space characters to the right of it until the string reaches the desired length. Display both the original and padded string in the page.

# 6

# Arrays

In Chapter 3, you learned about variables in PHP; in particular, you learned that a variable is a container that can store a single value. However, a couple of types of variables can store many values at once within a single variable. One such type is an object, which you discover in Chapter 8; the other is an array, which you explore in this chapter.

Arrays are a very powerful feature of any language, because they let you easily work with large amounts of data. For example, say you are writing a script that stores information about 100 customers. Rather than having to create 100 separate variables-$customer1, $customer2, and so on — to store the customers, you can create one array variable that holds information on all the customers at once.

Two specific features of arrays make them good for storing lots of data:

- Arrays can be of any length — An array can store one value, or millions of values, all referenced via a single variable name (for example, $customers). What's more, you can easily change the length — by adding or removing values — at any time

- It's easy to manipulate all values in an array at once — For example, you can loop through all the values inside an array, reading or changing them as you go. You can easily search for a value in an array, merge two arrays together, and much more

In this chapter, you:

- Learn how PHP arrays work

- Look at different ways of creating arrays
- Discover how to access the elements of an array
- Find out how to use loops (which you studied in Chapter 4) to work your way through all the elements of an array

# Part II: Learning the Language

- Take a look at multidimensional arrays, which let you create rich, complex data structures
- Explore some of PHP's powerful array-manipulation functions to do tricks such as sorting arrays and merging arrays together

# The Anatomy of an Array

Before diving into creating and using arrays, it's worth taking moment to explore the concept of an array in detail.

As already mentioned, an array is a single variable that can hold more than one value at once. You can think of an array as a list of values. Each value within an array is called an element, and each element is referred to by its index, which is unique to that array. To access an element's value — whether you're creating, reading, writing, or deleting — you use that element's index. In this sense, arrays share some similarity with strings, which you studied in the previous chapter. Just as you can access any character of a string by its index, you can access any element of an array using its element's index.

Many modern programming languages — including PHP — support two types of arrays:

- Indexed arrays — These are arrays where each element is referred by by a numeric index, usually starting from zero. For example, the first element has an index of 0, the second has an index of 1, and so

- Associative arrays — This type of array is also referred to as a hash or map. With associative arrays, each element is referred to by a string index. For example, you might create an array representing a customer's age and give it an index of "age"

Although PHP lets you create and manipulate both indexed and associative arrays, all PHP arrays are in fact of the same type behind the scenes. This can sometimes come in handy; for example, you can mix numeric and string within the same array, or treat an indexed array like an associative array. In practice, you generally want to work with one array type or another, and it helps to think of indexed and associative arrays as different types of arrays.

> index is often referred to as a key. Typically, a numeric index is called an index and a string index is called a key; however there's no hard-and-fast rule with this. You'll see both terms used interchangeably in this book and elsewhere.

The actual values stored in elements can be of any type, and you can mix types within a single array. So, for example, an array might contain a string as its first element, a floating-point number as its second element, and a Boolean value as its third.

# Creating Arrays

Powerful though they are, arrays in PHP are easy to create. The simplest way to create a new array variable is to use PHP's built-in array() construct. This takes a list of values and creates an array containing those values, which you can assign to a variable:

```
$authors = array("Steinbeck", "Kafka", "Tolkien", "Dickens");
```

# Chapter 6: Arrays

In this line of code, an array of four elements is created, with each element containing a string value.
The array is then assigned to the variable $authors. You can access any of the array elements via the single name, $authors, as you see in a moment.

This is an indexed array, which means that the array elements is accessed via its own numeric index, starting at zero. In this case, the "Steinbeck" element has an index of 0, "Kafka" has an index of 1, "Tolkien" has an index of 2, and "Dickens" has an index of 3.

If you want to create an associative array, where each element is identified by a string index rather than a number, you need to use the => operator, as follows:

```
$myBook = array( "title" => "The Grapes of Wrath", "author" => "John Steinbeck", "pubyear" => 1939 );
```

Many built-in PHP functions also create arrays. For example, file(), covered in Chapter 11, reads an entry into an array, one element per line.

# Accessing Array Elements

Once you've created your array, how do you access the individual values inside it? In fact, do you do this in the same way as you access the individual characters within a string:

```
$authors = array( "Steinbeck", "Kafka", "Tolkien", "Dickens" );
$myAuthor = $authors[0]; // $myAuthor contains "Steinbeck"
$anotherAuthor = $authors[1]; // $anotherAuthor contains "Kafka",
```

In other words, you write the variable name, followed by the index of the element in square brackets. If you want to access the elements of an associative array, simply use string indices rather than

```
$myBook = array( "title" => "The Grapes of Wrath", "author" => "John Steinbeck", "pubYear" => 1939 );
```

```
$myTitle = $myBook['title']; // $myTitle contains "The Grapes of Wrath"
$myAuthor = $myBook['author']; // $myAuthor contains "Steinbeck",
```

You don't have to use literal values within the square brackets; you can use any expression, as long as it evaluates to an integer or string as appropriate:

```
$authors = array( "Steinbeck", "Kafka", "Tolkien", "Dickens" );
$pos = 2;
echo $authors[$pos + 1]; // Displays "Dickens",
```

103

# Part II: Learning the Language
Changing Elements

As well as accessing array values, you can also change values using the same techniques. It's helpful to think of an array element as if it were a variable in its own right; you can create, read, and write its value at will.

For example, the following code changes of the third element in an indexed array from "Tolkien":

```
$authors = array("Steinbeck", "Kafka", "Tolkien", "Dickens" );
$authors[2] = "Melville";
```

What you wanted to add an author to fifth? You can just create a new element with an index of 4, as follows:

```
$authors = array("Steinbeck", "Kafka", "Tolkien", "Dickens" );
$authors[4] = "Orwell";
```

There's an easier way to add an element to an array — use square brackets with no index:

```
$authors = array("Steinbeck", "Kafka", "Tolkien", "Dickens" );
$authors[] = "Orwell";
```

When you do this, PHP knows that you want to add a new element to the end of the array, and automatically assigns the next available index — in this case, 4 to the element.

In fact, you can create an array from scratch by creating its elements using the square bracket syntax. The following examples all produce exactly the same array:

```
// Creating an array using the array() construct
$authors[2] = array("Steinbeck", "Kafka", "Tolkien", "Dickens" );

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
