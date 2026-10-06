# Part II: Learning the Language

A classic use of list() is with functions such as each() that return an indexed array of values. For example, you could rewrite the each() example from "Stepping Through an Array," earlier in this chapter, to use list():

```
$myBook = array( => "The Grapes of Wrath",
  "" => "John Steinbeck",
  "pubYear" => 1939 );
```

```
while ( list($key, $value) = each($myBook) ) {
  echo "<dt>$key</dt>";
  echo "<dd>$value</dd>";
}
```

# Summary

This chapter has introduced you to another important concept: arrays. These are special variables that can store more than one value, and you will find them all the time in your PHP scripts.

First you del into the anatomy of arrays, and learned the concepts of indexed and associative arrays. Then you learned how to create arrays in PHP, and access array elements using square brackets and array_slice(). Along the way you learned about a very useful PHP function, print_r(), that you can use to output entire arrays for debugging purposes.

Next, you discovered that every array has an internal pointer that refers to its elements, and learned how to use this pointer to move through the elements in an array using current(), key(), next(), prev(), end(), and reset(). You also used the handy foreach construct to loop through elements in an array.

Arrays get really powerful when you start beginning to produce multidimensional arrays. You studied how to create such arrays, as well as how to access their elements and loop through them.

Finally, you explored some PHP’s array-manipulation functions:

+   - Sorting functions — You learned at functions such as sort(), asort(), ksort() and array_multort()
- Functions for adding and removing elements — These include array_unshift(), array_shift(), array_push(), array_pop() and array_splice()
- array_merge() — This function is useful for merging two or more arrays together
- explode() and implode() — These let you convert between arrays and strings
- list() — You can use this to store array elements in a list of individual variables

PHP has a lot of array-related functions the ones covered in this chapter. It’s a good idea to explore the PHP manual at http://www.php.net/types.array to get an overview of the other array functions that PHP has to offer. Also, try following these exercises to test your array manipulation skills. You can find the solutions to these exercises in Appendix A.

The next chapter looks at the concept of functions in PHP, and how you show to create your own functions and build reusable chunks of code.