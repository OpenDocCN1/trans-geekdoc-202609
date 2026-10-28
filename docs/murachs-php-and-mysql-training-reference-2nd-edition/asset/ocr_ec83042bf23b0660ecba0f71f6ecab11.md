# The break statement in a while loop

```
while (true) {
    $number = mt_rand(1,10);
    if ($number % 2 == 0) {
        break;
    }
}
echo $number; // $number is between 1 and 10 and even
```

# The break statement in a for loop

```
$number = 13;
$prime = true;
for ($i = 2; $i < $number; $i++) {
    if ($number % $i == 0) {
        $prime = false;
        break;
    }
}
$result = ($prime) ? ' is ' : ' is not ';
echo $number . $result . 'prime.';
```

# The continue statement in a for loop

```
for ($number = 1; $number <= 10; $number++) {
    if ($number % 3 == 0) {
        continue;
    }
    echo $number . '<br>';
}
// Only displays 1, 2, 4, 5, 7, 8, and 10
```

# The continue statement in a while loop

```
$number = 1;
while ($number <= 10) {
    if ($number % 3 == 0) {
        $number++;
        continue;
    }
    echo $number . '<br>';
    $number++;
}
// Only displays 1, 2, 4, 5, 7, 8, and 10
```

# Description

+   - The break statement ends a loop. In other words, it jumps out of the loop.
+   - The continue statement ends the current iteration of a for or while loop, but allows the next iteration to proceed. In other words, it jumps to the start of the loop.
+   - When you’re working with nested loops, the break and continue statements apply only to the loop that they’re in.