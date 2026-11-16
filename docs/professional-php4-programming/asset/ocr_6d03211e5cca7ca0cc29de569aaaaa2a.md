# Precision Specifier

When using fractional/floating-point numbers, you can specify how many decimal places the number should be displayed with. The specifier is written as a decimal point, followed by an integer specifying the number of decimal places which will be displayed. This specifier can also be used to format strings, and it specifies the maximum number of characters from a supplied string which will be included.

# Type Specifier

The type specifier is used to indicate the type of data which will be supplied in the argument, and, in the case of an integer, which mode it should be displayed in. It can be one of the following characters:

+   - b – an integer presented as a binary number
+   - c – an integer presented as the character with that ASCII value
+   - d – an integer presented as a decimal number
+   - f – a floating-point value presented as a decimal fraction (with a decimal point)
+   - o – an integer presented as an octal number
+   - s – a string
+   - x – an integer presented as a hexadecimal number (with lowercase letters)
+   - X – an integer presented as a hexadecimal number (with uppercase letters)

In addition, to include a literal percentage character in a formatted string, you must write a double percent (%%).

Let's have a look at some examples of the sprintf()/printf() functions now. We mentioned that they could be used to format dates or currencies, so let's look at some examples of this now, starting with a date:

```
$day = 1;
$month = 2;
$year = 2001;
printf("%02d/%02d/%04d", $month, $day, $year);
```

This produces the following output:

```
01/02/2001
```

The format includes three conversion specifications, one for the month, one for the day, and one for the year. We are formatting the month and day as two-digit integers, and the year as a four-digit integer.
In order to do this, we need to specify that the integers should be padded out to a minimum length, with zeroes on the left. So, the conversion specification for the month, for example, looks like this:

```
%02d
```

The first character is a zero, and is the padding specifier. There is no alignment specifier, because we want the padding to be added to the beginning of the number. We'll add a minimum width specifier, which is 2.
We're formatting an integer, so we don't need a precision specifier. Then the last character is the type specifier, d, which tells the printf() function to format the number as a decimal integer.