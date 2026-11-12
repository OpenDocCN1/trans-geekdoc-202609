```
```php
<?php
$yourbossincome = 2000000;
print $yourbossincome."<br>";
$yourbossincome = "way too much for so little work";
print $yourbossincome."<br>";
?>
```
```

This code results in the following output in your Web browser:

```
2000000
way too much for so little work
```

You can see that I used the same variable. First, I put the number 2000000 in it, and then I put the string "way too much for so little work" in it. PHP can handle this change in type just fine, unlike strongly-typed languages such as C++ and Pascal.

But be careful, though, because by doing this, strange things can happen (in addition to your getting fired for complaining about your boss). For example, look carefully at the following code:

```
$yourbossincome = 2000000;
print $yourbossincome - 1000000;
print "\n<br>\n";
$yourbossincome = "way too much for so little work";
print $yourbossincome - 1000000;
```

![](bbox=[0.06, 0.55, 0.16, 0.6])

# Hexing and "octing" your numbers

If you want to use hexadecimal and octal numbers in your PHP program, you can. (If you're not familiar with hexadecimal and octal numbers, you can skip this sidebar.) To store the hexadecimal number 3C in a variable, for example, simply precede the number with a 0x, as in the following statement:

$number = 0x3c;

Remember, however, that if you print out this variable with a print statement, you'll see the decimal equivalent, in this case, 60.

You can also store octal numbers. You do this by preceding the number with a 0, as in the following statement:

$number = 012;

Make sure that you don't precede base-10 integers with a 0. The number 012 is not the decimal number 12; it's the octal number 12, which corresponds to the decimal number 10.

Remember: Do not put a 0 at the beginning of your numbers. Do not try to write a 10 as 010, or your PHP processor will store a different number entirely. Be careful!