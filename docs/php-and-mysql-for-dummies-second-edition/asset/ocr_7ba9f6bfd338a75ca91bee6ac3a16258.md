# Using function calls

*Functions* are blocks of statements that perform certain specified tasks. You can think of functions as mini-programs or subprograms. The block of statements is stored under a function name, and you can execute the block of statements any place you want by *calling* the function by its name. (For details on how to use functions, check out the section, “Using Functions,” later in this chapter.)

You can call a function by listing its name followed by parentheses, like this:

```
functionname();
```

For instance, you might have a function that gets all the names of customers that reside in a certain state from the database and displays the names in a list in the format *last name, first name*. You write the statements that do these tasks and store them as a function under the name `get_names`. Then when you call the function, you need to specify which state. You can use the following statement at any location in your program to get the list of customer names from the given state, which in this case is California:

```
get_names('CA');
```

The value in the parentheses is given to the function so it knows which state you’re specifying. This is *passing* the value. You can pass a list of values.

PHP provides many built-in functions. For example, in Chapter 6, I discuss a built-in function called `unset`. You can uncreate a variable named `$testvar` by using this function call:

```
unset($testvar);
```

# Using PHP Arrays

Arrays are complex variables. An *array* stores a group of values under a single variable name. An array is useful for storing related values. For instance, you can store information about a shirt (such as size, color, and cost) in a single array named `$shirtinfo`. Information in an array can be handled, accessed, and modified easily. For instance, PHP has several methods for sorting an array.

The following few sections give you the lowdown on arrays.