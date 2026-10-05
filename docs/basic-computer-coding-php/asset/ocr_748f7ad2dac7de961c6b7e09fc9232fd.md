We define an endless while loop. There is only one way to jump out of a such loop—using the break statement. We choose a random value from 1 to 30 and print it. If the value equals to 22, we finish the endless while loop.

```
$ php testbreak.php
6 11 13 5 5 21 9 1 21 22
We might get something like this.
```

In the following example, we print a list of numbers that cannot be divided by 2 without a remainder.

```
testcontinue.php
<?php
$num = 0;

while ($num < 1000) {
    $num++;
    if (($num % 2) == 0) continue;
    echo "$num ";
}
echo "\n";n
?>
```

We iterate through numbers 1..999 with the while loop.

```
if (($num % 2) == 0) continue;
```