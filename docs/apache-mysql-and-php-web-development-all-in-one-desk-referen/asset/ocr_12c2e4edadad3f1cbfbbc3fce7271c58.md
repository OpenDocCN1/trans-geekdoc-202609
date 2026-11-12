The division operator always does floating-point division; even when you use integers, it yields a float. Consider this example:

```
<?php
$a = 5;
$b = 2;
print $a / $b;
?>
```

Although $a and $b are both integers, the result of $a / $b is not a rounded form of 2.5 — say, 3. Rather, the result *is* 2.5, which is a float. That's because with division, the PHP processor treats both variables involved as floats, even if they're integers. If you need an integer version of a floating-point answer, you have two options. You can simply truncate it, as follows:

```
print floor($a / $b);
```

Or you can round it:

```
print round($a / $b);
```

The difference is that rounding approximates floating-point numbers to the nearest integer (less than 0.5 rounds down; 0.5 and higher rounds up). Thus, 2.5 rounds to 3. Floor, on the other hand, just chops off the decimal, meaning 2.5 truncates to 2. In other words, round($a) gives you the same as floor($x + 0.5).

There has been lots of discussion online about the potential problems with the lack of a true division operator. Because the division operator uses floating points, and because floating points are known for not being absolutely accurate, people worry about losing information in their integral division problems. However, my advice is this: If you're writing a software package that requires absolute precision with integers, please use the BCMath library and don't rely on the built-in integer types. Here's a short example of the BCMath library's integral division function:

```
$bca = "5";
$bcb = "2";
print bcdiv($bca, $bcb);
```

These statements output the result of dividing integer $bca by integer $bcb. In this case, the result is 2, which is the expected answer. If you had used a slash (as in $bca / $bcb), you would get 2.5, which is not an integer.