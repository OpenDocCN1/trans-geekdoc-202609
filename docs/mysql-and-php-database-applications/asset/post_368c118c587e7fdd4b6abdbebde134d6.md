
## Chapter 4: Getting Started with PHP — Variables

```php
else
    echo $row[$i];
    echo "<td>\n";
}
echo "</tr>\n";
}
echo "</table>";
```

Note that the exclamation point (!) means "not". So the phrase if(!isset($var)) will test true if the variable is not set.
If you wish to destroy a variable, use the unset function.

## empty()

The empty() function overlaps with the isset() function. It tests true if a variable is not set, contains an empty string, or has a value of 0. It is useful for, among things, processing form data. If you want to determine if the user put in a text field you could use something like this:

```php
if(empty($first_name))
{
    echo "Please enter your first name. It is a required field";
    exit;
}
```

## is_int()

This tests whether a variable is an integer. It has two synonyms: is_integer() and is_long(). You may need this function to troubleshoot a script when you're not sure if a variable is an integer or a string containing numerals.

```php
$a = "222";
$b = 22;
```

Given two variable assignments, is_int($a) would test false and is_int($b) would test true.

## is_double()

This function tests whether a variable is a floating-point (or double) number. It has two synonyms: is_float() and is_real().

## is_string()

This function tests whether a variable is a text string.

## is_array()

This function tests whether a variable is an array. This is used frequently in the course of this book. A good example can be found in Chapter 6, in the discussion of the implode() function.

## is_bool()

This function tests whether a variable is boolean, (contains either TRUE or FALSE). Note that the following examples are not boolean.

```php
$a = "TRUE";
$b = "FALSE";
```

In Chapter 6 you will see a variety of functions that return FALSE on failure. In these, FALSE is a boolean value.

## is_object()

Returns true if the variable is an object. See Chapter 6 for a discussion of objects and object-oriented programming if you don't know what an object is.

## gettype()

This function will tell you the type of variable you have. It will return the expected values (string, double, integer, array, or boolean), and it can also return types related to object-oriented programming (object, class). There will be more information on PHP object-oriented programming in Chapter 6.

Note that gettype() returns a string. So the following would test TRUE and print "Yes".

```php
$str = "I am a string";
$type = gettype($str);
if ($type == "string") {
  echo "Yes";
}
```

## Changing Variable Types

There are three ways to change the type of any variable.

## Type casting

By placing parentheses containing the variable type you require before the variable name, you will change the variable type.

```php
$a = 1;
$b = (string) $a;
echo gettype($a), "<br\n";
echo gettype($b), "<br\n";
```

This code would print,

```
integer
string
```

Using this method you can cast a variable as an array, a double, an integer, an object, or in the preceding code, a string.

## settype()

This function takes two arguments. The first is a variable name. The second specifies the variable type. The advantage of this function over casting is that settype() will return a value of FALSE if the conversion fails. There is no way to detect a failed casting. It can take the same types as listed in type casting.

```php
$a = 1;
settype($a, "string");
```

## intval(), doubleval(), and stringval()

Finally, if you don't have enough to evaluate variable types, use one of these functions. They do not actually change the type of the variable, but return a value of the specified type. So in the following, you can be sure, $a will be treated like an integer.

```php
$a = "43";
$b = (intval($a) * 2);
```

## Variable Variables

PHP includes variable variables, which, in the wrong hands, could be used to write the most incomprehensible code imaginable. It enables you to take the contents of a variable and use them as variable names. Two consecutive dollar signs let PHP know to take the value of the variable and use that as a variable name. The following creates a variable name $foo with the value of "bar":

In the context of a database application, variable variables might be used to create series of variables against which you compare other variables. In the following, $firstrow is an associative array.

```php
$firstrow = array("firstname"->...
```

```php
while (list($field,$value) = each($firstrow))
{
  $field = "first_field";
  $$field = $value;
}
```

```php
echo $first_name, ". ", $first_lastname;
```

When run through the while loop, the following variables would be created and printed.

```
$first_name = "jay";
$first_lastname = "greenspan";
```

## Summary

If you read this chapter attentively (or even if you didn't) you should have a pretty good idea of how to work with PHP variables.

PHP does a better job than any scripting language in making variables easy to access and process. If you want to get a feel of how PHP variables are used, take a look at Chapter 8, the first application in the book. Many of the functions and concepts presented here are put to work. By flipping back and forth between this chapter and these scripts, you will see how variables are used and how scripts come together.

One very important point: This chapter did not discuss variable scope, which is a very important topic. See Chapter 7, when we discuss functions, for an explanation of this topic.

## Chapter 5

## Control Structures

### IN THIS CHAPTER

- Understanding the syntax of if statements
- Determining true and false values with PHP
- Learning PHP loops
- Choosing loops to use in your scripts

CONTROL STRUCTURES ARE THE BUILDING blocks of programming languages. PHP has all of the control structures needed to make a language work. If you're familiar with C or Perl, none of the features we discuss in this chapter should come as much of a surprise. However, if you're approaching PHP from a background in VBScript or Visual Basic, the syntax will probably be different from what you're used to. If you find the syntax to be a little heavy at first, stick with it. You might find that the extra brackets and parentheses actually help you write readable code.

## The if Statements

The if statement is pretty much the cornerstone of all programming languages. In PHP, an if statement typically takes this basic form:

```php
if (condition)
{
    actions to perform if condition is true.
}
```

After the word “if” is a set of parentheses. Within those parentheses is the single condition or set of conditions to be tested. If the condition is evaluated as being true, the code within the curly braces will be executed. The following will test true and print “I’m True!” to a Web page.

```php
<?php
$foo = 100;
$bar = 10;
if ($foo>$bar)
```

```php
(
  echo "I'm True!";
)
?>
```

This is clear enough. But before we mention the complexities of the if statement, you should know how PHP determines whether a condition is true or false.

## Determining true or false in PHP

The next section will show the operators commonly used in if statements. These are fairly intuitive. In the preceding code example, 100 is greater than 10, so it will test true. No problem But there's a bit more to these tests in PHP.
The words TRUE and FALSE also carry the expected meaning.

```php
if (TRUE)
{
  echo "Yup"; //this will be printed
}
if (FALSE)
{
  echo "Nothing doing"; //this will not be printed
}
```

But you are not limited to simple mathematical operators or the words TRUE and FALSE when testing a true or false condition. As you saw in Chapter 4, you will often test for the existence of a variable using isset() or empty(). These functions, like many others in PHP, will return a value of 0 if the condition is false, and a value of 1 if the condition is true. The whole will actually print "1".

```php
$myvar = "I am setting a variable";echo isset($myvar);
```

In PHP "0" is equivalent to false. As you can guess, "1" is equal to true. But it's not just "1" that is non-zero, non-empty value tests as true. This gives you some flexibility in your tests.

When working with pages, you'll be doing some sort of text manipulation. Often you'll need to test whether the string you're writing has a certain structure. For example, you might want to test if a string contains certain characters. You could use the regular expression functions for this, but you could also use the strstr() function takes takes arguments, both of them strings. It searches for the first occurrence of the string in the first argument. It returns the string in the second argument plus all of the characters following that string. However, if the string isn't found, the function will return FALSE. In the example below strstr() returns the "text string".
