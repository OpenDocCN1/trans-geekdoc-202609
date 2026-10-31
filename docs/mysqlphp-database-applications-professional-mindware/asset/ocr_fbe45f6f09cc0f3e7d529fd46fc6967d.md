# Function Basics

Functions all take the same basic form.

```
return_type function_name(argument1, argument2, argument3)
```

First there is the function’s name; note that the name of the function is not case-sensitive. However, we don’t know of any programmer who ever uses uppercase letters to refer to a built-in function.

Next there is a set of parentheses. Every function will have a set of parentheses marking the beginning and end of the arguments.

# Arguments

So what’s an argument? An argument is simply a value that the function is expecting. Depending on the purpose of the function, it may expect zero, one, two, three, or more arguments, and any of the arguments may be any variable type—maybe a string, maybe an integer, or maybe an array. To give you a better idea of what arguments are, let’s look at a very useful function for string handling.

The str_replace() function is extremely helpful. Let’s say you had the following string:

```
$str = "My name is Jay.";
```

Say that in the $str variable you need to replace “Jay” with “John”. Within $str you need to search for “Jay” and replace it with “John”. Here, you would expect a function to take three arguments: the string to be searched for, the replacement string, and the string to be searched through. It so happens that in PHP, the arguments come in this order:

```
str_replace(string to search for, replacement string, string to be searched through);
```

Or to put it in practice:

```
$str = "My name is Jay.";
$new_str = str_replace("Jay", "John", $str);
```

Keep in mind that certain functions will have optional arguments and a few will take no arguments at all. The substr() function, for example, has an optional third argument. This function returns a portion of a string by its ordinal references. To get everything from the second character to the next-to-last character, you would use the following:

```
//note, the first character in the string is 0
$new_str = substr ($str_var,1,-1);
```