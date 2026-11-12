+   * **Float**: This is a type for floating point numbers that include a decimal point.
+   * **String**: This is a type for strings of characters.

(Remember that a single variable can hold any type. You can store an integer in a variable and later put a string in the same variable.) Here’s an example that demonstrates each of the four types:

```
<html><body>
<?php

$myiq = 206;
$myname = "Wiley";
$mytemp = 98.6;
$AmICool = true;

print $myiq."<br>";
print $myname."<br>";
print $mytemp."<br>";
print $AmICool."<br>";
?>
</body></html>
```

After the PHP processor gets its hands on this code, you end up with the following output in your browser window:

206
Wiley
98.6
1

This output probably is what you expect, although the last item may seem a little strange. The print statement prints Boolean variables as either 0 for false or 1 for true.

**TIP** Note that in the preceding PHP code, I’m using a little trick called the concatenation operator, which is the dot, or period. You can see this in each of the print lines, such as `print $myiq . "<br>";`. This is the way you print multiple items — in this case $myiq and the “<br>” string — with a single print statement. I talk more about this concatenation operator in the section, “Concatenating and squishing together strings,” later in this chapter.

**TECHNICAL STUFF** The `integer` type in PHP is a 32-bit signed integer. If you need more precision than 32 bits, use the BCMath library. (Note that the documentation states that this type is platform dependent, although these days you can pretty much always expect it to be signed 32 bits.) The floating point numbers are 64 bits. (Again, this is platform dependent, but unless you’re using a bizarre computer, you can expect 64 bits.)