If you have an expression that tests for equality, use two equal signs, as in if ($a == $b). This is different from a variable assignment, where you always use a single equal sign, as in $a = 10;. But if you want to test for inequality, use an exclamation point (called a bang) followed by an equal sign, as in if ($a != $b). Other languages (including Perl and C++) use this same syntax.

# Looping with while

If you have some code that you want repeated over and over while a certain condition is true, and want the code to stop after the condition is no longer true, you can use a while loop.

Here's a quick example of a while loop:

```
```html
<html><title>While Your Power Bill Runs</title>
<body>
    Welcome to your power bill. The following
    numbers represent your expected bill for
    the next several months. Be sure to pay
    up or we'll shut it off.<br>
<?php
    $power = 2;
    while ($power < 10000) {
        print "$". $power .".00<br>\n";
        $power *= 2;
    }
?>
</body>
</html>
```
```

This example initializes the variable $power to 2 and then begins calculating powers of 2, representing ... your power bill' The loop runs as long as $power is less than 10,000. First, it prints out the value, formatted to look like a dollar amount, and then it multiplies the value by 2. It then repeats the process — printing and then multiplying — as long as the value is less than 10,000.

If the condition in a while loop is never true, the code inside the while loop never executes. Thus, in the following code, the print statement never runs:

```
```php
$x = 10;
while ($x < 5) {
    print "phoops\n";
}
```
```