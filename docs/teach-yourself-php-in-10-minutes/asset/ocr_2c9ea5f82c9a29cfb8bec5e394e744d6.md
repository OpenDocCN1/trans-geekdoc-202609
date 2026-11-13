# Table 6.1. `printf` Format Characters

| Character | Meaning |
|---|---|
| b | A binary (base 2) number |
| c | The ASCII character with the numeric value of the argument |
| d | A signed decimal (base 10) integer |
| e | A number displayed in scientific notation (for example, 2.6e+3) |
| u | An unsigned decimal integer |
| f | A floating-point number |
| o | An octal (base 8) number |
| s | A string |
| x | A hexadecimal (base 16) number with lowercase letters |
| X | A hexadecimal (base 16) number with uppercase letters |

Suppose you use the %d format specifier instead of %f to display the value of $price :

```
$price = 5.99;
printf("As a decimal, the price is %d", $price);
```

In this case, PHP will treat the argument passed as an integer, so only the whole part of the value will be displayed. The output produced is as follows.

As a decimal, the price is 5

**Decimals** The %d format string represents a decimal integer, with *decimal* referring to base 10 numbers and not decimal points. There are different format specifiers to display numbers in base 16 (*hex*, %x ), base 8 (*octal* , %o ), and base 2 (*binary* , %b ).

# Format Codes

A format specifier can also include optional elements to specify the padding, alignment, width, and precision of the value to be displayed. This allows you to carry out some very powerful formatting.