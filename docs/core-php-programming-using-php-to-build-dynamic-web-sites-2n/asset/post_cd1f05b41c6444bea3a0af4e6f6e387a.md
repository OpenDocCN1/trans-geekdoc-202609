
# Core PHP Programming

If PREG_PATTERN_ORDER is used, the first element of the matches array will contain an array of all matches against the full pattern. The other elements of the array will contain arrays of matches against subpatterns.

If PREG_SET_ORDER is used, each element of the matches contains an array organized like that preg_match. The first element is the entire matching string. Each subsequent element contains the match against the subpattern for match.

# preg_quote(string text)

The preg_quote function returns text with backslashes inserted before character that have special meaning in the functions in this section. The special characters are:

+ * \ \\ + ? [ ] $ ( ) } = ! <> | :

# preg_replace(string pattern, string replacement, string text)

The preg_replace function is equivalent to ereg_replace. Each time the pattern matches a substring within the text argument, it is replaced with the replacement argument. The text argument is unchanged, but the altered version is returned.

If the pattern contains subexpressions in parentheses, the replacement argument may contain a special code for specifying which expression to replace. The form is to use two backslashes before a single digit, zero through nine. Zero matches the entire expression; one through nine each match the first subexpressions, respectively. Subexpressions are numbered left to right, which accounts for nested subexpressions.

```php
// swap newlines for break tags
$text = "line1\nline2\nline3"
print(preg_replace("|\n", "<BR>", $text));

print("<HR>\n");
```

```php
// mix up these words
$text = "one two three four"
print(preg_replace("|([a-z]+) ([a-z]+) ([a-z]+)", "\\4 \\2 \\1 \\\3", $text));
```

# preg_split(string pattern, string text, integer limit)

The preg_split function returns an array of substrings from the text argument. The pattern argument will be used as a field delimiter. The optional limit argument sets the maximum number of elements to return. This function is equivalent to split.

```php
<?php
$paragraph = "This is a short paragraph. Each ";
$paragraph .= "sentence will be extracted by ";
$paragraph .= "you will be amazed!";
$sentence = preg_split("\\.\!\\!\\//", $paragraph);

for($index = 0; $index < count($sentence)) {
    print("$index. $sentence[$index]<BR>\n");
}
?>
```

# Chapter 10. MATHEMATICAL FUNCTIONS

Common Math

Random Numbers

Arbitrary-Precision Numbers

The math functions fall into three categories: common mathematical operations, random numbers, and special functions for handling numbers of arbitrary precision.

# Common Math

The functions in this section offer most of the common mathematical operations that are of arithmetic, geometry, and trigonometry. Most of these functions work on either doubles or integers. The return type will be the same as the argument. Unless a specific type is called for, I've written "number" to indicate that either an integer or a double is expected.

# number abs(number value)

The abs function returns the absolute value of a number. This is the number itself if it's positive, or the number multiplied by negative one (-1) if negative.

```php
<?php // prints 13
print (abs(-13));
?>
```

# double acos(double value)

The acos function returns the arc cosine of the value argument. Trying to find the arc cosine of a value greater than one or less negative one is undefined.

Figure 10-1. acos.

# Core PHP Programming

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_292_0.png)

acos acos values from -1 to 1

```php
// print("<TABLE BORDER=\"1\">\n");
print("<TR><TH>x</TH><TH>acos (x)</TH></TR>\n");

for($index = -1; $index <= 1; $index += 0.25) {
    print("<TR\n");
```

# double asin(double value)

The asin function returns the arc sine of the value argument. Trying to find the arc sine of a value greater than one or less than negative one is undefined.

```php
<?php // print asin values from -1 to 1
print("<TABLE ORDER=\"1\">\n");
print("<TR><TH x=\"x\"></TH><TH>asin(x)</TH></TR>\n");

for($index = -1; $index <= 1; $index += 0.25) {
    print("<TR>\n");
    print("<td>\$index</TD>\n");
    print("<td>" . asin($index) . "</TD>\n");
    print("<TR>\n");
}

print("</TABLE>\n");
?>
```

# double atan(double value)

The atan function returns the arc tangent of the value argument.

```php
<?php // print asin values from -1 to 1
print("<TABLE ORDER=\"1\">\n");
print("<TR><TH x=\"x\"></TH><TH>atan(x)</TH></TR>\n");

for($index = -1; $index <= 1; $index += 0.25) {
    print("<TR>\n");
    print("<td>\$index</TD>\n");
    print("<td>" . atan($index) . "</TD>\n");
    print("<TR>\n");
}

print("</TABLE>\n");
?>
```

# double atan2(double x, double y)

The atan2 function returns the arc tangent of the quotient of y/x, taking into account the signs of both arguments to determine the correct quadrant of the result.

# double pow(double base, double exponent)

The pow function returns the base raised to the power of the exponent.

# double sqrt(double value)

The sqrt function returns the square root of a number. If the value is negative, it returns NAN.

# number max(number value1, number value2)

The max function returns the larger of the two numbers.

# number min(number value1, number value2)

The min function returns the smaller of the two numbers.

# integer rand(integer min, integer max)

The rand function returns a random integer between min and max (inclusive).

# integer mt_rand(integer min, integer max)

The mt_rand function returns a random integer using the Mersenne Twister generator.

# integer random_int(integer min, integer max)

The random_int function returns a random integer between min and max (inclusive), and is cryptographically secure.
