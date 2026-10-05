
# KNOWLEDGE CHECK

1. Returns a string argument with trailing blank space removed, is a behavior of

- a. ltrim() function
- b. chop() function
- c. rtrim() function
- d. Both B and C

2. A sequence of characters that is treated as a unit is called

- a. Arrays
- b. Functions
- c. Methods
- d. Strings

3. ltrim() returns its string argument with

- a. Leading blank space removed
- b. Trailing blank space removed
- c. Numerical values
- d. None of them

4. When two strings are exactly equivalent, strcmp() returns what?

- a. Returns a string
- b. Returns 0
- c. Returns 1
- d. Returns nothing

5. For finding out one string is equal to another string, which function we can use?

- a. strpos()
- b. strpos()
- c. str()
- d. All of them

# Basic Computer Coding: PHP

# REVIEW QUESTIONS

- 1. Discuss on the single quoted string.
- 2. Write a program on double quoted string technique.
- 3. What do you understand by the variable parsing?
- 4. Explain the procedure of complex (curly) syntax.
- 5. How to string access and modify by character?

# CHECK YOUR RESULT

- 1. (d) 2. (d) 3. (a) 4. (b) 5. (b)

# REFERENCES

- 1. Andrei Zievski. “The Good, the Bad, and the Ugly: What Happened to Unicode and PHP 6”. Retrieved 2014-02-09.
- 2. “Basic Coding Standard”. PHP Framework Interoperability Group. Retrieved 2016-01-03.
- 3. http://php.net/manual/en/language.types.string#phplanguage.types.string.details
- 4. http://php.net/manual/en/language.types.string#phplanguage.types.string.details
- 5. https://docs.python.org/2/library/string.html
- 6. https://techterms.com/definition/string
- 7. https://www.cloudways.com/blog/php-string-functions-with-examples/
- 8. https://www.guru99.com/php-strings.html
- 9. https://www.javatpoint.com/php-string
- 10. https://www.techspedia.com/definition/3853/parse
- 11. https://www.tutorialspoint.com/php/php_strings.htm
- 12. “Resetting PHP 6”. There have been books on the shelves purporting to cover PHP 6 since at least 2008. But, in March 2010, the PHP 6 release is not out — in fact, it is not even close to out. Recent events suggest that PHP 6 will not be released before 2011 — if, indeed, it is released at all.

```
'country' => 'US',
'age' => 25

echo json_encode($object);

// Echoes {
// "name":"Jane Doe",
// "country":"US",
// "age":25
// }
// Just like we love it!
```

# CHAPTER 5

# PHP ARRAYS

> "As Bromberger observed, rules are understood to be elements of the computational systems that determine the sound and meaning of the infinite array of expressions of a language; the information so derived is accessed by other systems in language usage."

—Noam Chomsky

# Learning Objectives

After studying this chapter, you will be able to:

- Discuss about array functions
- Understand the arrays

# INTRODUCTION

PHP supports both scalar and compound data types. In this chapter, we will discuss one of the compound types: arrays. An array is a collection of data values organized as an ordered collection of key-value pairs. It may help to think of an array, in loose terms, like an egg carton. Each compartment of an egg carton can hold an egg, but it travels around as one overall container. And, like an egg carton does not have to contain eggs (you can put anything in there, like rocks, snowballs, four-leaf clovers, or nuts & bolts), so too an array is not limited to one type of data. It can hold strings, integers, Booleans, and so on. Plus, array can also contain other arrays, but more on that later.

This chapter talks about creating an array, adding and removing elements from an array, and looping over the contents of an array. Because arrays are very common and useful, there are many built-in functions that work with them in PHP. For example, if you want to send email to more than one email address, you will store the email addresses in an array and loop through the array, sending the message to the current email address. Also, if you have a form that permits multiple selections, the items selected are returned in an array.

Configuration is an arrangement of functional units according to their nature, number, and chief characteristics.

# 5.1 ARRAY FUNCTIONS

These functions allow you to interact with and manipulate arrays in various ways. Arrays are essential for storing, managing, and operating on sets of variables.

# 5.1.1 Installation

There is no installation needed to use these functions; they are part of PHP core.

# 5.1.2 Configuration

This extension has no configuration directives defined in php.ini.

# 5.1.3 Array Constants

| Sr.No | Constant | Description |
|---|---|---|
| 1 | CASE_LOWER | Used with array_change_case() to convert array keys to lowercase |
| 2 | CASE_UPPER | Used with array_change_case() to convert array keys to uppercase |
| 3 | SORT_ASC | Used with array_multisort() to sort in ascending order |
| 4 | SORT_DESC | Used with array_multisort() to sort in descending order |
| 5 | SORT_REGULAR | Used to compare items normally |
| 6 | SORT_NUMERIC | Used to compare items numerically |
| 7 | SORT_STRING | Used to compare items as strings |
| 8 | SORT_LOCALE | Used to compare items as strings, based on the locale |
| 9 | COUNT_NORMAL | |
| 10 | COUNT_RECURSIVE | |
| 11 | EXTR_WRITE | |
| 12 | EXTR_SKIP | |

# 5.1.4 List of Functions

| Sr.No | Function | Description |
|---|---|---|
| 1 | array() | Create an array |
| 2 | array_change_case() | Returns all keys in lowercase or uppercase |
| 3 | array_chunk() | Splits array into chunks |
| 4 | array_combine() | Creates an array using one array for keys and another for values |
| 5 | array_count_values() | Returns the number of occurrences for each value |
| 6 | array_diff() | Compares array values |
| 7 | array_diff_assoc() | Compares array keys and values |
| 8 | array_diff_key() | Compares array keys |
| 9 | array_diff_uassoc() | Compares array keys and values, with a user-made function, and returns the differences |
| 10 | array_diff_ukey() | Compares array keys, with an additional user-made function, and returns the differences |
| 11 | array_fill() | Fills an array with a specified number of items, with a specified value, to an array |
| 12 | array_fill_keys() | Fills an array, specifying keys |
| 13 | array_filter() | Filters elements of array using a user-made function |
| 14 | array_flip() | Exchanges all keys with their associated values |
| 15 | array_intersect() | Compares array values |
| 16 | array_intersect_assoc() | Compares array keys and values |
| 17 | array_intersect_key() | Compares array keys |
| 18 | array_intersect_uassoc() | Compares array keys and values, with a user-made function, and returns the differences |
| 19 | array_intersect_ukey() | Compares array keys, with an additional user-made function, and returns the differences |
| 20 | array_key_exists() | Checks if the specified key exists in the array |
| 21 | array_keys() | Returns all the keys of an array |
| 22 | array_map() | Sends each value of an array to a user-made function, which returns new values |
| 23 | array_merge() | Merges one or more arrays into one array |
| 24 | array_merge_recursive() | Merges one or more arrays into one array |
| 25 | array_multisort() | Sorts multiple or multi-dimensional arrays |
| 26 | array_pad() | Inserts a specified number of items, with a specified value, to an array |
| 27 | array_pop() | Deletes the last element of an array |
| 28 | array_product() | Calculates the product of the values in an array |
| 29 | array_push() | Inserts one or more elements to the end of an array |
| 30 | array_rand() | Returns one or more random keys from an array |
