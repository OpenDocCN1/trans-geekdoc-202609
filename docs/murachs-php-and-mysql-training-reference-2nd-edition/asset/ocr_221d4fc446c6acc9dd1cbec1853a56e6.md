# The parts of a format code

| Specifier | Required? | Description |
|---|---|---|
| % | Required | A percent sign always starts the format code. To code a percent sign within a format code, you can code two percent signs in a row (%%). |
| Sign | Optional | By default, the negative sign is displayed for negative numbers but no sign is displayed for positive numbers. To always display a sign, code a plus (+) or minus (-) sign. |
| Alignment | Optional | By default, the value is right-aligned. To align on the left, code a dash (-) character. |
| Padding | Optional | By default, the padding character is a space. To specify a different padding character, code a zero or a single quote (') followed by the padding character. |
| Width | Optional | To specify a minimum width, code an integer. |
| Precision | Optional | To specify precision, code a period (.) followed by an integer value. For a number, this indicates the number of decimal points. For a string, this indicates the maximum characters. Longer strings are truncated. |
| Data Type | Required | A code that specifies the data type. These data types are described in part 1 of this figure. |

# How to use the optional specifiers

```
$s1 = sprintf("%+d", 42);    // Returns '+42'
$s2 = sprintf("%+d", -42);   // Returns '-42'
$s3 = sprintf("%10s", 'PHP'); // Returns '       PHP'
$s4 = sprintf("%-10s", 'PHP'); // Returns 'PHP       '
$s5 = sprintf("%-.*10s", 'PHP'); // Returns 'PHP*******'
$s6 = sprintf("%6d", 42);    // Returns '    42'
$s7 = sprintf("%06d", 42);   // Returns '000042'
$s8 = sprintf("%02d-%02d-%04d", 3, 5, 2010); // Returns '03-05-2010'
$s9 = sprintf("%010.2f", 123.456); // Returns '0000123.46'
```

# How to generate a random HTML color

```
$color = '#';
for($i = 0; $i < 6; $i++) {
    $color .= sprintf("%x", mt_rand(0,15) );
}
echo $color;  // For example '#984e1e'
```