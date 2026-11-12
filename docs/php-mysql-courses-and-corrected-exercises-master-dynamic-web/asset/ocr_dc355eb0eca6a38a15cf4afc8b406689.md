The if keyword is followed by a condition in brackets (). If the condition evaluates to true, the block of code inside braces {} following if will be executed. Otherwise, if the condition evaluates to false, the block of code inside the {} braces following else will be executed.

The block of code inside the {} braces after the if statement contains the instructions to be executed if the condition is true.

The else keyword is used to define an alternative block of code that will be executed if the if condition is false.

The block of code inside the braces {} after the else contains the instructions to be executed if the condition in the if is false.

# Example:

```
<?php
$age = 14;
if ($age >= 18) {
  echo "You're over 18.";
} else {
  echo "You're a minor.";
}
?>
```

In this example, if the value of the variable $age is greater than or equal to 18, the message “You’re over