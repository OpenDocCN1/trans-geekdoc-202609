> > **TIP:** A pretty neat resource is the function table at http://www.zugeschaut-und-mitgebaut.de/php/.

# Function Basics

Functions all take the same basic form:

```
return_type function_name (argument1, argument2, argument3)
```

First, return_type is the type of output that the function returns when called: integer, Boolean, array, string, and so forth. These are called return values. Next is the function’s name; note that the name of the function is not case-sensitive.

Finally, following the function name is a set of parentheses. Inside the parentheses are any arguments required by the function, separated by commas. While having any arguments at all is optional, the parentheses themselves are not. We will discuss arguments first, followed by return values, because that’s the order in which the function deals with them.

# Arguments

An argument is simply a value (or a reference to a value) that the function is expecting. A function might expect zero, one, two, three, or more arguments, and any of the arguments can be of any variable type – it may be a string, an integer, an array, or something else. To give you a better idea of what arguments are, here’s an example: a function that does string handling.

The str_replace() function is extremely helpful. Suppose you have the following string:

```
$str = "My name is Jay.";
```

Say that in the $str variable you need to search for Jay and replace it with John. The function that does the replacement takes three arguments: the string to be searched through, the string to be searched for, and the replacement string. It so happens that in PHP, the arguments come in this order:

```
str_replace(string to search for, replacement string, string to be searched through);
```

Or, to put it in practice:

```
$str = "My name is Jay.";
$new_str = str_replace("Jay", "John", $str);
```