```
{
  global $$key;
  $key = $value;
}
```

This expects a result identifier gathered from mysql_query(). Assume that the query row prior to this function call return a single row. That row is assigned to an associative array named Row. Each column taken from the query (which is now in the associative array) and its value will be available as a global. This could be useful if the variables retrieved from the query are needed in many other functions. Note the use of variables in this code. See Chapter 5 for an explanation of this concept.

> > Tip: All of the Apache variables ($DOCROOT, $REQUEST_URI, and so forth) are available as globals. To use them within functions you will need to make the function aware of them.

# USING GLOBAL VARIABLES

Throughout the applications in this book you will see that global variables are used sparingly within functions. This is because it is easier to keep track of your variables if you are passing them through arguments and retrieving them through return values. If you start using globals extensively, you may find that your variables are returning unexpected values in different places—finding the functions that are causing the error can be a major pain.

Here's another reason to avoid globals when possible: You will be using the same variable name over and over and again. We don't know how many times in these applications the variable $query, $result, $row, or $i are used, but trust us when we say they are used frequently. All of kinds would be introduced into my life if we had to keep track of each time we used one of these variable names.

At times you will have little choice but to use global variables, before you do, make sure that you can't accomplish the same using variables of local scope.

# Object-Oriented Programming

A few years back there was a move toward object-oriented programming. Some people thought that the procedural approach—that is, coding strictly with functions—just wasn't enough. Therefore, the folks working on languages like C++ and Java popularized an approach that allows a developer to think about in a different way.