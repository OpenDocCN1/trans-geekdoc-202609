By the way, if you want to convert the newlines in a string to HTML `<br />` elements, you can use PHP's `nl2br()` function. This takes a string to convert as an argument and returns the string with all newlines converted to `<br />` s.

You can also pass an optional fourth argument to `wordwrap()`. If this argument is `true` (the default is `false`), the function always wraps the string to the specified line width, even if this means splitting words that are longer than the line width. Here's an example:

```
```
$myString = "This string has averylongwordindeed.";

echo wordwrap ( $myString, 10, "<br />" );
echo "<br /><br />";
echo wordwrap ( $myString, 10, "<br />", true );
```
```

Here's what this code outputs:

```
```
This
string has
averylongwordindeed.

This
string has
averylongw
ordindeed.
```
```

# # Formatting Numbers with number_format()

PHP's `number_format()` function gives you a convenient way to format numbers in an easy-to-read way, with thousands separators and rounded to a specified number of decimal places. In its most basic form, you just need to pass the number to format as a single argument, and the function returns the formatted string:

```
```
echo number_format( 1234567.89 ); // Displays "1,234,568"
```
```

Note that this rounds to the nearest whole number. If you'd rather include some decimal places, specify the number of places as a second, optional argument:

```
```
echo number_format( 1234567.89, 1 ); // Displays "1,234,567.9"
```
```

Finally, you can change the characters used for the decimal point and thousands separator by passing two more optional arguments. For example, the following code formats the number using the French convention of a comma for the decimal point and a space for the thousands separator:

```
```
echo number_format( 1234567.89, 2, ",", " " ); // Displays "1 234 567,89"
```
```

You can pass empty strings for either of these two parameters, so you can format a number with no thousands separators if you like:

```
```
echo number_format( 1234567.89, 2, ".", "" ); // Displays "1234567.89"
```
```