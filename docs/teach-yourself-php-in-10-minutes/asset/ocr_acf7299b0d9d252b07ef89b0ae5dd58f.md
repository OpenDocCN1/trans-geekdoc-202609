Analyzing Data Types In practice, you will not use `settype` and `gettype` very often because you will rarely need to alter the data type of a variable. This book covers this topic early on so that you are aware that PHP does assign a data type to every variable.

# Type Juggling

Sometimes PHP will perform an implicit data type conversion if values are expected to be of a particular type. This is known as *type juggling* .

For example, the addition operator expects to sit between two numbers. String type values are converted to double or integer before the operation is performed, so the following addition produces an integer result:

```
echo 100 + "10 inches";
```

This expression adds 100 and 10 , and it displays the result 110 .

A similar thing happens when a string operator is used on numeric data. If you perform a string operation on a numeric type, the numeric value is converted to a string first. In fact, you already saw this earlier in this lesson, with the concatenation operatorthe value of $weight that was displayed was numeric.

The result of a string operation will always be a string data type, even if it looks like a number. The following example produces the result 69 , butas `gettype` shows$number contains a string value:

```
$number = 6 . 9;
echo $number;
echo gettype(6 . 9);
```

We will look at the powerful range of operators that are related to numeric and string data types in PHP in Lessons 5 , "Working with Numbers," and 6 , "Working with Strings."

# Variable Variables

It is possible to use the value stored in a variable as the name of another variable. If this sounds confusing, the following example might help:

```
$my_age = 21;
$varname = "my_age";
echo "The value of $varname is ${$varname}";
```