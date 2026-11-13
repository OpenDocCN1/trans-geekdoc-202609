satisfy the condition.

**Operator Symbols** Note that the logical AND and OR operators are the double symbols `&&` and `||` , respectively. These symbols, when used singularly, have a different meaning, as you will see in Lesson 5 , "Working with Numbers."

# # Multiple Condition Branches

By using an `else` clause with an `if` statement, you can specify an alternate action to be taken if the condition is not met. The following example tests the value of `$number` and displays a message that says whether it is greater than or less than 10:

```
```php
$number = 16;
if ($number < 10) {
     echo "$number is less than ten";
}
else {
     echo "$number is more than ten";
}
```
```

The `else` clause provides an either/or mechanism for conditional statements. To add more branches to a conditional statement, the `elseif` keyword can be used to add a further condition that is checked only if the previous condition in the statement fails.

The following example uses the `date` function to find the current time of day`date("H")` gives a number between 0 and 23 that represents the hour on the clockand displays an appropriate greeting:

```
```php
$hour = date("H");
if ($hour < 12) {
    echo "Good morning";
}
elseif ($hour < 17) {
    echo "Good afternoon";
}
else {
    echo "Good evening";
}
```
```

This code displays `Good morning` if the server time is between midnight and 11:59, `Good afternoon` from midday to 4:59 p.m., and `Good evening` from 5 p.m. onward.

Notice that the `elseif` condition only checks that `$hour` is less than 17 (5 p.m.). It does not need