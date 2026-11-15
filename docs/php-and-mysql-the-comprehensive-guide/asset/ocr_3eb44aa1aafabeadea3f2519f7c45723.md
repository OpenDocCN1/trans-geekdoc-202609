+   * **Binary**
+   
+   This system uses only 0 and 1. If there is a 1, the respective number is present; if there
+   is a 0, it is not present. The numbers are read from right to left. The first digit on the
+   right stands for 1, the one to the left for 2, the one to the right for 4, the one to the left
+   for 8, and so on. Therefore, binary 101 converts to decimal 5.

+   * **Octal**
+   
+   This number system is based on the number eight. An octal number is also read
+   from right to left. To convert it into a decimal number, multiply the right-hand digit
+   by 1, the digit to the left by 8, the digit next to it by 64, the digit next to it by 512, and
+   so on. Therefore, octal 143 converts to decimal 99.

> **Note**
> 
> As of PHP 8.1, there is an innovation for the notation of octal numbers. They are now
> notated with a leading 0 as before, but with a lowercase o afterward:
> 
> $octal = 0o143;

Converting manually from the decimal number system to these three systems would
be unnecessarily complicated. PHP helps you here with three conversion functions:

+   * dechex(number)
+   * decbin(number)
+   * decoct(number)

> **Note**
> 
> The conversion functions return a string as the result. There are no data types for hexa-
> decimal, binary, and octal numbers in PHP. The back-conversion functions also use a
> string as a parameter.

There are also three functions for the reverse path. The names always follow the same
convention. The number system from which the conversion is made is at the front:

+   * hexdec(String)
+   * bindec(String)
+   * octdec(String)

The following example shows a simple form (see Figure 9.1) with which you can convert
a decimal number into the other three number systems.

```
<?php
if (isset($_POST["send"])) {
    $decimal = $_POST["decimal"];
    $hexa = dechex($decimal);
```