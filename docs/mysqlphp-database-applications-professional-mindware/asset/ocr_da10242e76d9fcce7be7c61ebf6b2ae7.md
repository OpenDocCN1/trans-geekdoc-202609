```
{
echo "Between 50 and 99.";
}
}
```

![](bbox=[0.18, 0.22, 0.26, 0.28])

Are you getting a parse error you can't identify? Make sure you have an identical number of opening and closing curly braces and parentheses. If you have, say, five closing curly braces in a page and only three opening, you haven't closed one of your code blocks.

# Function calls

Indenting code should not stop at code blocks. Often you will need to use nested function calls or complex variables that take up several lines. You will be much happier in your coding life if you use indents in these situations. Take a look at the following, which is borrowed from the Catalog application.

```
$file_ext = strtolower(
    substr($file
    , strrpos($file,".")
    )
);
```

The purpose of this code is pretty simple: it takes the name of a file and assigns its extension (the characters following the final dot (".")) to $file_ext. It takes three separate built-in PHP functions to get this done. PHP will execute the innermost level first. There, strrpos() finds the numeric position of the final dot. For instance, in the stringmyfile.jpg, it would return 6. Then the substr() function would return only the characters following the dot. Finally, that string would be set to lower case characters.

This could be written on one line, but as you can see, it becomes rather difficult to read.

```
$file_ext = strtolower(substr($file, strrpos($file,".")));
```

![](bbox=[0.18, 0.78, 0.26, 0.85])

Or maybe you find this easier to read. A lot of things we'll talk about in this chapter are matters of personal preference. The important thing is that you spend a lot of time considering how to make your code as readable as possible.