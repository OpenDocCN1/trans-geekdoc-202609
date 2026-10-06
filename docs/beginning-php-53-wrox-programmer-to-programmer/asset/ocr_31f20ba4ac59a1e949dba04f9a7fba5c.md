# Chapter 5: Strings

```
<?php
$Number = 123.45;
printf( "Binary: %b<br>", $Number );
printf( "Character: %c<br>", $Number );
printf( "Decimal: %d<br>", $Number );
printf( "Scientific: %e<br>", $Number );
printf( "Float: %f<br>", $Number );
printf( "Octal: %o<br>", $Number );
printf( "String: %s<br>", $Number );
printf( "Hex (lower case): %x<br>", $Number );
printf( "Hex (upper case): %X<br>", $Number );
?>

<body>
</html>
```

You can see the result in Figure-5.

![](bbox=[0.276, 0.368, 0.821, 0.643])

Figure 5-3

# Specifying Signs

By default, printf() displays negative numbers with a minus ( ) symbol in front of them, but doesn't put a plus (+ ) symbol in front of positive numbers. To change printf() 's behavior so that it always displays a sign, use the sign specifier, +, in front of the type specifier. Here's an example:

```
printf( "%d<br>", 123 ); // Displays "123"
printf( "%d<br>", -123 ); // Displays "-123"
printf( "%+d<br>", 123 ); // Displays "+123"
printf( "%+d<br>", -123 ); // Displays "-123"
```