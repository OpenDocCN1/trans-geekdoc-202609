# PHP with echo statements that trace the execution of the code

```
```php
// calculate the future value
$future_value = $investment;
echo '$future_value: ' . $future_value . '<br>';
echo '$interest_rate: ' . $interest_rate . '<br>';
echo '$years: ' . $years . '<br>';
echo 'For loop for calculating future value is starting...<br><br>';
for ($i = 1; $i <= $years; $i++) {
    $future_value = ($future_value + ($future_value * $interest_rate));
    echo '$i: ' . $i . '<br>';
    echo '$future_value: ' . $future_value . '<br>';
}
```
```

# The data displayed in a browser

![](bbox=[0.071, 0.301, 0.799, 0.685])

# Description

+   - An easy way to trace the execution of a PHP application is to insert echo statements at key points in the code.
+   - The echo statements can display the values of variables or display messages that indicate what portion of the code is being executed.
+   - When you see an incorrect value displayed, there is a good chance that you have a logic error between the current echo statement and the previous one.

Figure 6-3 — An easy way to trace the execution of your PHP code