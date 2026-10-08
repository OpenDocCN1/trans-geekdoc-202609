
## Core PHP Programming

This is commonly referred to as a variable reference. Changes made to referenced variables change the original.

To demonstrate this idea, imagine we wanted something like "10,000" from an input field we stripped commas from numbers. But if we knew it was ten thousand, not. We could build the function by passing a string and returning it with the commas. But in this case we want to pass the variable and have it changed. Listing 4.3 demonstrates this functionality.

It is also possible to make an argument optional. Many built-in functions provide this functionality. The date function is one you should be familiar with—you pass one or two arguments. The first argument is the format of the return value. The second argument is the timestamp, a date expressed since January 1, 1970. If the second argument is omitted, the current time is used.

You do this in yours by providing a default value using the = operator immediately after the argument. The right side of = is a literal value that the variable will be. Listing 4.4. Since arguments are matched up to right, you must provide a default value for every argument after the first with a default value.

## Listing 4.3 Passing Arguments by Reference

```php
<?php
function stripCommas(&$inputString)
{
    $inputString = ere_replace(",", "", $inputString);

    $myNumber = "10,000";

    stripCommas($myNumber);
    print($myNumber);
}
?>
```

You may set an argument to unset by making it equal to NULL, a special. Listing 4.5 demonstrates this functionality.

Other named arguments, you may also access arguments by their position using three functions: `func_get_arg`, `func_get_args`, `func_num_args`. These functions are described in Chapter 8. You may fetch either one argument at a time using `func_get_arg`, or fetch them all as an array using `func_get_args`. To find out how many arguments were passed, use `func_num_args`. Calling a function with a number of arguments different from the prototype is not an error if you write your function that way.

## Listing 4.4 Arguments with Default Values

```php
<?php
function printColored($Text)
{
    print("<FONT COLOR=$Color>$Text</FONT>");
}

printColored("This is black text");
print("<BR\n");

printColored("This is blue text", "blue");
print("<BR\n");
?>
```

## Listing 4.5 Using unset with a Default Argument

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_85_0.png)

```php
<?php
function myPrint($text, $size=NULL)
{
  if(isset($size))
    print("<FONT SIZE=$size>$text</FONT>");
  else {
    print($text);
  }
}
myPrint("Test");
print("<BR\n");

myPrint("Test", 5);
print("<BR\n");
?>
```

You might wonder why you'd ever want to pull arguments out using the functions mentioned instead of naming them in the declaration. It's possible that you do not know how many arguments will be given. Consider a function that creates a list, given any number of items. You could first place those items in an array, then pass the array to the function, which in turn would pull the items out of the array. Alternatively, you could write a function that accepted a variable number of arguments, as I have in Listing 4.6.

## Listing 4.6 Function with Variable Number Arguments

```php
<?php
function makeList()
{
    print("<OL\n");

    for($i=0; $i<$func_num_args(); $i++) {
        print("<li>" . func_get_arg($i) . "</li>\n");
    }
    print("</OL\n");
}

makeList("PHP", "MySQL", "Apache");
?>
```

## Recursion

Your functions may make calls to other functions, and they may also make calls to themselves. The process of a function calling itself is recursion. This circular definition leads to elegant algorithms. The problem is broken down into a small task that's repeated many times.

Recursive definitions are common in mathematics. Consider this definition of an integer: the sum or difference between one and any other integer is an integer. Is three an integer? Yes, because one plus one must be an integer, with one being two. And the sum of one and two must also be an integer.

Recursion is a difficult concept to understand, but it usually takes clear code. Take a look at Listing 4.7. The function checkInteger takes a number as input. We know that the difference between integer and one is an integer. If the function gets a number bigger than one, it checks the number minus one. If we start with a number less than zero...

## Listing 4.7 Using Recursion

```php
<?php
function checkInteger($number)
{
    if ($number > 1) {
        return checkInteger($number - 1);
    } elseif ($number < 0) {
        return checkInteger($number + 1);
    } else {
        return $number;
    }
}
?>
```
