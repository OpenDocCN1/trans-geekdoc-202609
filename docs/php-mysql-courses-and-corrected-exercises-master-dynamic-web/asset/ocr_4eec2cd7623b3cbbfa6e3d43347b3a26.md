```
}
```

You can call the **print _r($tab)** function to see the result.

# Exercise 20: function and array (foreach)

Write a PHP function that takes an array of numbers as input and returns the sum of all these numbers.

# Correction

```
<?php
function sum_tab($tab) {
    $sum = 0;
    foreach ($tab as $number) {
        $sum += $number;
    }

    return $sum;
}
```

An example of use:

```
$my_array = array(1, 2, 3, 4, 5);
```