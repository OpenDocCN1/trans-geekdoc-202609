# Core PHP Programming

# Listing 5.6 Creating and Referencing a Multidimensional Array

```
<?php
$Cities = array(
    "California"=>array(
        "Martinez",
        "San Francisco",
        "Los Angeles"
    ),
    "New York"=>array(
        "New York",
        "Buffalo"
    )
)

print($Cities["California"][1]);

```

# Casting Arrays

You can cast an array as another data type to get results of various usefulness. When you cast an array as an integer, double or boolean, you will get a value of 1. When you cast an array as a string, you will get the word Array. This is useful as an indicator of when you have mistakenly used an array as a string. An array will be promoted to a string containing Array if you use it in a context that demands a string, such as in a print statement. You can't use an array in a context that demands a number, such as with the addition operator. This will cause an error. Listing 5.7 explores casting an array as other data types.

The most useful cast of an array you can perform is to an object. The elements of the array will become properties of the object. However, elements indexed by values illegal inaccessible. These values are not lost, and if you recast the variable as an array, they will become available again. Objects are discussed in Chapter 6.

# Listing 5.7 Casting Arrays as Other Data Types