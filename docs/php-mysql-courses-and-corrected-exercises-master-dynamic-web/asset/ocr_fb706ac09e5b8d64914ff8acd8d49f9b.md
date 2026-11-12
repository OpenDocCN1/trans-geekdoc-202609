function to perform operations. Here's an example of a function taking two arguments:

```
<?php
//Definition of the function that calculates the sum
function addition($a, $b) {
  $sum = $a + $b;
  echo "The sum is: $sum ";
}

addition(10, 20); // Call function with arguments
?>
```

In this example, we define a function called addition() which takes two parameters, $a and $b, representing the two numbers to be added. Inside the function, we add the two parameters and store the result in a variable $sum. Then, we use the echo statement to display the result along with a message indicating the calculated sum.

After defining the function, we call it, passing two values, 10 and 20, as arguments. The function additions these two values and displays the result, "The sum is: 30".