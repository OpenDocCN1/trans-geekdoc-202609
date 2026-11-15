Have you already calculated the power in your head? PHP says the result is 8.

> **Note**
> 
> As an alternative, there is also the `**` operator for calculating a power. You can read more about this in Chapter 5.

The intdiv() function is practical. It performs an integer division. Its first parameter is the number to be divided; its second is the divisor. The return is the integer result of the division. The following example therefore returns 4.

```
<?php
$a = 8;
$b = 2;
echo intdiv($a, $b);
?>
```

# Listing 9.2 Division with "intdiv()" ("intdiv.php")

If it is divided by 0, a fatal error of the type DivisionByZeroError is thrown.

If you need more than PHP offers, write your own function. If you have several of them, it is best to save them in an external script file and load them as required with include() or require().

For a simple example of a useful function, think about the addition of any number.

```
<?php
function add() {
    $numbers = func_get_args();
    $sum = 0;
    foreach ($numbers as $number) {
        $sum += $number;
    }
    return $sum;
}
echo add(2, 10, 66, 5, 23);
?>
```

# Listing 9.3 A Custom Mathematical Function ("custom_function.php")

In the preceding example, mental arithmetic becomes more difficult. The result is 106.

# 9.1.2 Constants

Some mathematical constants are used frequently, are difficult to calculate, or both. Therefore, PHP provides some predefined constants, which we list in Table 9.1.