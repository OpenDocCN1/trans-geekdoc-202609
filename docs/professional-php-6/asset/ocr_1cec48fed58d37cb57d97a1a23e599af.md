corresponding binary bits of each value are subject to the traditional Boolean comparison (with 1 meaning true and 0 meaning false). If $var1 is 34 and $var2 is 11, then the following applies:

```
34       =   00100010
11       =   00001011
34 & 11  =   00000010   =   2
```

Accordingly, the bitwise logic of 34 and 11 yields 2, because it is only in the 2 column where both bits are 1 in each number.

What does this have to do with constants? Put simply, it enables you to combine constants to form a single value (which consists of the arithmetic sum of its constituent constants), and then easily determine later what those constituent constants are.

If each constant represents the incrementing decimal value of a single bit of a binary number (essentially, a power of 2), then when summed together, the resulting binary number will have bits set to 1 representing those constants that have been included in that sum:

```
CONST_A =   1   =   00000001
CONST_B =   2   =   00000010
CONST_C =   4   =   00000100
CONST_D =   8   =   00001000
CONST_E =   16  =   00010000
```

For example, say that you want to define a parameter consisting of constants B, D, and E combined (whatever that might mean). Simply add the values 2, 8, and 16 together to get a value of 26. Take a look at what 26 looks like in binary, next to its constituent components:

```
CONST_B =   2   =   00000010
CONST_D =   8   =   00001000
CONST_E =   16  =   00010000
CONST_B+D+E =   26  =   00011010
```

Notice that you can clearly recognize that the constituent constants of the combination are B, D, and E; but how do you test for this in code?

Enter and run the following code from the command line (rather than in a Web browser). Normally, you'd just type php at a command prompt to do this, but if the PHP executable isn't in your path, you'll need to hunt it down first — try /usr/local/php/bin on UNIX:

```
<?php
define('CONST_A', 1);
define('CONST_B', 2);
define('CONST_C', 4);
define('CONST_D', 8);
define('CONST_E', 16);

$myCombinedConstant = CONST_B + CONST_D + CONST_E;

if ($myCombinedConstant & CONST_A) {
    print "Combined constant contains A\n";
};
```