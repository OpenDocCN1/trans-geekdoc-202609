
## Other skills for working with strings and numbers

This topic presents some other skills that you can use for formatting strings and numbers as well as converting strings to numbers.

### How to use the sprintf function to format strings and numbers

Part 1 of figure 9-12 shows how to use the sprintf function to format strings and numbers. You can use this function to code a single *format string* that formats multiple string and numeric values based on their corresponding *format codes*.

When you call the sprintf function, you pass the format string as the first parameter. Then, you pass the values to be formatted as the remaining parameters. The sequence of the parameters must match the sequence of their format codes in the format string.

The simplest format code consists of the percent sign (%) followed by one of the data type characters listed in this figure. For example, a code of %s formats the value as a string. Similarly, a code of %d formats the value as an integer.

The first example shows a sprintf function that formats two values. Here, the first parameter contains a format string that contains two format codes. Then, the next two parameters supply the values to be formatted. The first value is a string that’s formatted as a string, and the second value is an integer that’s formatted as an integer.

The second example shows how to use the sprintf function to format values as other data types. For example, the first statement formats an integer as a string. The second and third statements format floating-point numbers as strings. The fourth and fifth statements format floating-point numbers in exponential notation and in standard notation. The sixth statement formats an integer as an ASCII character. And the seventh and eighth statements format an integer as a hexadecimal value.

If you want to include a percent sign in the format string, you can code two percent signs. This indicates that you want to include a single percent sign instead of starting a new format code. In this figure, the format string for the variable named $s9 converts a floating-point number to a string and includes a percent sign after the number.

### The sprintf function

| Name | Description |
|---|---|
| `sprintf($format, $val1[, $val2 ...])` | Returns a string that contains one or more values that are formatted as specified by the `$format` parameter. |

### Data type code

| Character | Description |
|---|---|
| `s` | Formats the value as a string. |
| `d` | Formats the value as an integer. |
| `f` | Formats the value as a floating-point number. |
| `e` | Formats the value using exponential notation. |
| `c` | Formats an integer value as its corresponding ASCII character. |
| `b` | Formats an integer value as a binary number. |
| `o` | Formats an integer value as an octal number. |
| `x` | Formats an integer value as a hexadecimal number (lowercase). |
| `X` | Formats an integer value as a hexadecimal number (uppercase). |

### A sprintf function that formats two values

```php
$message = sprintf('The book about %s has %d pages.', 'PHP', 800);
```

### How to use sprintf to convert numbers to strings

```php
$s1 = sprintf('It cost %s dollars', 12);          // It cost 12 dollars
$s2 = sprintf('%s', 4.5);                        // 4.5
$s3 = sprintf('%s', 9451000.000000);             // 9451000
$s4 = sprintf('%f', 9.451e6);                    // 9451000.000000
$s5 = sprintf('%e', 9451000.000000);             // 9.451000e+6
$s6 = sprintf('%c', 65);                         // A
$s7 = sprintf('%x', 15);                         // f
$s8 = sprintf('%X', 15);                         // F
$s9 = sprintf('%s%%', 4.5);                      // 4.5%
```

### Description

- Within a sprintf function, the *format string* can contain one or more format codes.
- A *format code* always begins with the `%` sign and ends with a character that specifies the data type for the value.
- To code a percent sign (`%`) within a format string, code two percent signs.

Figure 9-12 — How to use the sprintf function (part 1 of 2)

The table in part 2 of figure 9-12 shows all the parts of a format code. As you’ve learned, all format codes begin with a percent sign and end with a character that specifies the data type. However, between these required parts of a format code, you can use the optional specifiers shown in this figure.

The first example shows how to use the optional format specifiers. For instance, the first two statements use the plus sign (+) to include a positive or negative sign in the formatted value.

The next three statements format a string with a minimum width of 10 characters. Here, the third statement aligns the string to the right by padding it with spaces on the left. The fourth statement aligns the string to the left by padding it with spaces on the right. And the fifth statement aligns the string to the left by padding it with asterisks (*) on the right.

The next two statements format integer values with a width of 6 characters. Here, the sixth statement aligns the integer to the right by padding it with spaces on the left. The seventh statement also aligns the integer to the right, but pads the value with zeros.

The eighth statement contains three format codes that format a date. These three format codes format three integers by padding them with zeros on the left. Here, the first two format codes are two characters wide, and the third format code is four characters wide. Note that the dashes between the format codes are literal values that are displayed in the string that’s returned by the sprintf function.

The ninth statement formats a floating-point value. This value is formatted so it is ten characters wide and has two decimal places. Note that the sprintf function rounds the value from 123.456 to 123.46 to get the correct number of decimal places.

The last example shows how to generate a random HTML color value. Here, the first statement stores a pound sign (#) in the $color variable. Then, this code executes a loop six times. Within the loop, there is a single statement that generates a random number between 0 and 15, uses the sprintf function to format the number as a hexadecimal digit, and appends the hexadecimal digit to the $color variable.

### The parts of a format code

| Specifier | Required? | Description |
|---|---|---|
| % | Required | A percent sign always starts the format code. To code a percent sign within a format code, you can code two percent signs in a row (%%). |
| Sign | Optional | By default, the negative sign is displayed for negative numbers but no sign is displayed for positive numbers. To always display a sign, code a plus (+) or minus (-) sign. |
| Alignment | Optional | By default, the value is right-aligned. To align on the left, code a dash (-) character. |
| Padding | Optional | By default, the padding character is a space. To specify a different padding character, code a zero or a single quote (') followed by the padding character. |
| Width | Optional | To specify a minimum width, code an integer. |
| Precision | Optional | To specify precision, code a period (.) followed by an integer value. For a number, this indicates the number of decimal places. For a string, this indicates the maximum characters. Longer strings are truncated. |
| Data Type | Required | A code that specifies the data type. These data types are described in part 1 of this figure. |

### How to use the optional specifiers

```php
$s1 = sprintf("%+d", 42);        // Returns '+42'
$s2 = sprintf("%+d", -42);       // Returns '-42'
$s3 = sprintf("%10s", 'PHP');    // Returns '       PHP'
$s4 = sprintf("%-10s", 'PHP');   // Returns 'PHP       '
$s5 = sprintf("%-'*10s", 'PHP'); // Returns 'PHP*******'
$s6 = sprintf("%6d", 42);        // Returns '    42'
$s7 = sprintf("%06d", 42);       // Returns '000042'
$s8 = sprintf("%02d-%02d-%04d", 3, 5, 2010); // Returns '03-05-2010'
$s9 = sprintf("%010.2f", 123.456); // Returns '0000123.46'
```

### How to generate a random HTML color

```php
$color = '#';
for($i = 0; $i < 6; $i++) {
    $color .= sprintf("%x", mt_rand(0,15) );
}
echo $color;  // For example '#984e1e'
```
