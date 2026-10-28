
## How to convert strings to numbers

Figure 9-13 shows how to convert strings to numbers. One way to do that is to use type casting. To cast a value from one type to another, code the data type in parentheses followed by the value to convert. In this figure, for example, the examples show how to cast a string to the integer (int) data type or the floating-point (float) data type.

The first example shows how to convert string values to integer values. Here, the second statement shows that floating-point values are truncated, not rounded. Then, the third and fourth statements show that the conversion process stops when any non-numeric text is encountered. The fifth and sixth statements show that the resulting value is 0 if the string doesn’t begin with a number. The seventh statement shows that values that are too large to be stored as integers return a value of PHP_INT_MAX. And the last two statements show that only base 10 numbers can be converted correctly using type casting.

The second example shows how to use the intval function to convert a string to an integer. This function follows the same rules as type casting when performing the conversion.

The third example shows how to convert strings to floating-point values by using type casting. Here, the second statement shows that any non-numeric text stops the conversion process. The third statement shows that the resulting value is 0 if the string doesn’t begin with or contain a number. The fourth statement shows that type casting can convert a value that uses exponential notation. And the fifth statement shows that the resulting value is INF if the value is too large to be represented as a floating-point value.

The fourth example shows how to use the floatval function to convert a string to a floating-point value. Like the intval function, this function follows the same rules as type casting when performing the conversion.

### Two functions for converting strings to numbers

| Function | Description |
| --- | --- |
| `intval($var)` | Returns an integer value for the `$var` parameter. |
| `floatval($var)` | Returns a floating-point value for the `$var` parameter. |

### How to convert a string to an integer

### Using type casting

```
$value_1 = (int) '42';                  // Result is 42
$value_2 = (int) '42.5';                // Result is 42
$value_3 = (int) '42 miles';             // Result is 42
$value_4 = (int) '2,500 feet';            // Result is 2
$value_5 = (int) 'miles: 42';             // Result is 0
$value_6 = (int) 'miles';                // Result is 0
$value_7 = (int) '10000000000';          // Result is PHP_INT_MAX
$value_8 = (int) '042';                  // Result is 42
$value_9 = (int) '0x42';                 // Result is 0
```

### Using the intval function

```
$value = intval('42');                 // Result is 42
```

### How to convert a string to a floating-point number

### Using type casting

```
$value_1 = (float) '4.2';                // Result is 4.2
$value_2 = (float) '4.2 gallons';         // Result is 4.2
$value_3 = (float) 'gallons';              // Result is 0
$value_4 = (float) '1.5e-3';               // Result is 0.0015
$value_5 = (float) '1e400';                 // Result is INF
```

### Using the floatval function

```
$value = floatval('4.2');                // Result is 4.2
```

### Description

- You can use *type casting* to convert, or cast, a value from one type to another. To do that, code the data type within parentheses just before the value that you want to convert. Here, you can use the int keyword for the integer data type and the float keyword for the floating-point data type.
- You can also use the intval and floatval functions to convert a value from one type to another. The result is the same as it is with type casting.
- When converting strings to numbers, any text after the number is ignored.
- When converting strings to numbers, strings that don’t start with a number are converted to a value of 0.
- When converting strings to floating-point values, the string can use exponential notation.
- If a value is too large to fit in its data type, PHP converts integer values to the PHP_INT_MAX constant and floating-point values to the INF constant.

Figure 9-13  How to convert strings to numbers

## Perspective

In this chapter, you learned new ways to work with strings and numbers. When you combine these skills with those you learned in section 1, you have the skills that you need for working with strings and numbers. In the next chapter, you’ll learn the skills for working with dates and times.

Although this chapter includes the essential functions for working with strings and numbers, PHP provides many more. As a result, if you find yourself faced with a task, and it seems like PHP might provide a function that can help you with that task, there’s a good chance the function exists. So, before you write your own code, you should search the online PHP reference manual to see if you can find the function you need. If you can find it, you can save a lot of time and effort.

## Terms

| | |
| --- | --- |
| variable substitution | integer |
| interpolation | whole number |
| heredoc | floating-point number |
| nowdoc | float |
| escape sequence | double |
| length of a string | real number |
| substring | exponential notation |
| position in a string | mantissa |
| trim a string | exponent |
| pad a string | format string |
| tab-delimited data | format code |
| ASCII character set | type casting |

## Summary

- When you use PHP, you can create strings by using single quotes, double quotes with *variable substitution*, *heredoc* syntax, and *nowdoc* syntax.
- *Escape sequences* provide a way to insert special characters into text strings. The htmlentities function provides a way to convert escape sequences and HTML characters to HTML character entities that display properly in a browser.
- PHP provides many functions for working with strings, including functions for getting the *length* and *substrings* of a string; for searching and replacing strings; for *trimming*, *padding*, and modifying strings; for converting strings to and from arrays; for comparing two strings; and for formatting strings based on format codes.
- PHP provides functions for working with both *integer* and *floating-point numbers*. It also provides functions for generating random numbers.
- You can use *type casting* to convert a string to an integer or floating-point number. You can also use the intval and floatval functions for these conversions.

## Exercise 9-2    Write code that works with numbers

In this exercise, you can write some PHP code that works with numbers.

### Open and test the application

- 1. Start the Chrome browser and run the application in the ex_starts/ch09_ex2 directory. This should display a page that allows you to enter three numbers and provides starting values for the three numbers.
- 2. Click on the Submit button. Note that this displays a message that includes the values of the three numbers but doesn’t include the values for the rest of the message.

### Write the code that processes the data entered by the user

- 3. Open the index.php file for this application and review the code. Note that it doesn’t process the data. Instead, it just displays the data on the form.
- 4. Open the number_tester.php file for this application and review the code. Note that the PHP code that displays the $message variable uses the nl2br function to convert new line characters to <br> tags.
- 5. Add the code that uses the data that’s entered into the text box controls to display a message that’s formatted like this:

```
Number 1: 78
Number 2: -105.33
Number 3: 0.0049

Number 2 ceiling: -105
Number 2 floor: -106
Number 3 rounded: 0.005

Min: -105.33
Max: 78

Random: 86
```

When formatting this message, use escape sequences to insert new line characters.

- 6. Make sure the user enters all three numbers and that these numbers are valid.
- 7. Make sure the rounded number is rounded to 3 decimal places.
- 8. Make sure the random number is a number between 1 and 100.
- 9. Test the application to make sure it works correctly with the default values and also with other values.
