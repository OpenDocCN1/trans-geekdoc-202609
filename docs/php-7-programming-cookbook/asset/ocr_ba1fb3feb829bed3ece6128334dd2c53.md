You can actually do the same thing in PHP 5. Two lines of code are required, however:

```
$func = $freq->bindTo($access);
$func($line);
```

Performance is **20% to 50%** slower than using `call() in PHP 7.

Finally, we reverse-sort the array, but maintain the keys. The output is produced in a simple `foreach()` loop:

```
arsort($access->frequency) ;
foreach ($access->frequency as $key => $value) {
    printf('$16s : %6d' . PHP_EOL, $key, $value);
}
```

The output will vary depending on which `access.log` you process. Here is a sample:

![](bbox=[0.3, 0.49, 0.69, 0.78])