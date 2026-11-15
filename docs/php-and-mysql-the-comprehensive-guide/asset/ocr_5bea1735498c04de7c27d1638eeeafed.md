Here is another example for better understanding:

```
```php
$sum = 200;
$format = "%07.2f";
printf($format, $sum);
```
```

This supplies the following:

0200.00

A 0 is inserted at the beginning as the minimum width is 7 and zeros are used instead of spaces for padding. Two decimal places are inserted after the decimal point. The data type is converted to a floating-point number.

sprintf(default string, parameter) is closely related to printf(), but it returns the result—namely, the formatted string—as the return value.

```
```php
$sum = 200;
$format = "%.2f Euro";
$result = sprintf($format, $sum);
echo $result;
```
```

# Listing 6.40 "sprintf() ("sprintf.php")"

The preceding lines provide the following string as the value for the $result variable, which is then output:

200.0 Euro

Note
The functions mentioned here also include vsprintf(Format, Array) and vprintf(Format, Array). They convert an array with arguments into a string with the specified format.

# 6.2.4 "print_r" and "var_dump"

The print_r(variable) and var_dump(Variable) functions provide the structure and content of a variable as output. They are well suited to analyzing more complex data types such as objects and arrays (see Figure 6.27).

```
```php
<?php
$days = array("Monday", "Tuesday", "Wednesday");
print "print_r: ";
print_r($days);
```
```