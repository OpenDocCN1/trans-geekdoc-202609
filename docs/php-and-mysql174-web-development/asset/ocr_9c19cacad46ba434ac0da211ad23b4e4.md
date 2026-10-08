# Chapter 4 String Manipulation and Regular Expressions

The advantage of printf() is that you can use a more useful conversion specification to specify that $total is a floating-point number and it should have two decimal places after the decimal point, as follows:

```
printf("Total amount of order is %.2f", $total);
```

Given this formatting, 12.4 stored in $total, this statement will print 12.40.

You can have multiple conversion specifications in the format string. If you have n conversion specifications, you will usually have n arguments for the format string. Each conversion specification will be replaced by a reformatted argument in the order they are listed. For example:

```
printf("Total amount of order is %.2f (with shipping %.2f)",
$total, $total_shipping);
```

Here, the first conversion specification uses the variable $total, and the second uses the variable $total_shipping.

Each conversion specification follows the same format, which is
%[ 'padding_character'] [-width] [.precision] type

All conversion specifications start with a % symbol. If you want to print a % symbol, you need to use %%%. By default, only values that are negative show a sign (in

The padding_character is optional. It is used to pad your variable to the width you have specified. An example would be to add leading zeros to a number like a counter. The default padding character is a space. If you are specifying a space or zero, you do not need to prefix it with the apostrophe ('). For any other padding character, you need to prefix it with an

The – symbol is optional. It specifies that the data in the field will be left-justified rather than right-justified, which is the default.

The width specifier tells printf() how much room (in characters) to leave for the variable to be substituted in.

The precision specifier should begin with a decimal point. It should contain the number of places after the decimal point you would like displayed.

The final part of the specification is a type code. A summary of these codes is shown in Table 4.3.

Table 4.3 Conversion Specification Type Codes
| Type | Meaning |
|---|---|
| % | A literal character. |
| b | Interpret as an integer and print as a binary number |