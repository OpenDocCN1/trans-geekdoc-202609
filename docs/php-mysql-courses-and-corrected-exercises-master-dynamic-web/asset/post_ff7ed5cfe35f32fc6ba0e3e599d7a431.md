
## Ternary conditional structures

![](img/caba2aa22f5409ba73dea47176330677_124_0.png)

PHP's ternary conditional structures offer a concise and efficient way of writing conditional statements in a single line of code. They are particularly useful when you need to evaluate a simple condition and return a value depending on the result of that condition.

The general syntax of a ternary conditional structure is as follows:

```php
$variable = (condition) ? value_if_true : value_if_false;
```

Let's explain this syntax:

The condition is evaluated first.

- If the condition is true, the value following the question mark "?" is assigned to the variable $variable.
- If the condition is false, the value following the ":" is assigned to the variable $variable.

Here's a simple example to illustrate the use of ternary conditional structures in PHP:

```php
<?php
$age = 20;
$message = ($age >= 18) ? "You are an adult." : "You are a minor";
echo $message;
?>
```

In this example:

- If the age is greater than or equal to 18, the message "You are an adult." is assigned to the $message variable.
- Otherwise, the message "You are a minor" is assigned to the variable $message.

In this example, with the value of the variable $age equal to 20, the condition $age >= 18 is evaluated as true. Consequently, the expression following the "?" operator is assigned to the $message variable, giving the following result:

You are an adult.

Ternary conditional structures can make your code more concise and readable when used appropriately. However, it's important not to overuse them in order to maintain code readability. Use them judiciously for simple, straightforward conditions.

## Conclusion

In this chapter on conditional structures in PHP, we've explored the various tools and techniques available for controlling the flow of program execution. From simple if-else statements to more complex structures like switch and match, we've seen how to write logical conditions to make decisions based on input data. By understanding these concepts, PHP developers can create more robust and flexible scripts, capable of adapting to different situations and producing customized results according to the needs of the application. By making judicious use of conditional structures, developers can make their programs more efficient and intelligent, offering a better user experience.

## EXERCISES

### Exercise 4

Write a script that checks whether a number stored in a variable is positive, negative or zero.

### Exercise 5

Write a program to check students' skill development assessed on a scale of 100 using conditional instructions.

- If the competency level is 80% or more, the student will be in the first group.
- If the degree of competence is between 50% and 80%, the student will be in the second group.
- If the degree of competence is between 30% and 50%, the student will be in the third group.
- If the competency level is below 30%, the student will fail.

### Exercise 6

Write a conditional script to test whether a number is a multiple of both 3 and 5.

### Exercise 7

Write a program to display the day of the week (e.g. Monday) based on numbers, using switch statements.

- Day 1 will be considered as Monday
- If the number is not between 1 and 7, display "invalid number" by default.

## Chapter 3

### Loops in PHP

Welcome to the chapter on loops in PHP! Loops are essential tools in program development, as they enable instructions to be executed repeatedly depending on certain conditions. Whether you're a beginner or an experienced developer, this chapter will guide you through the different types of loops available in PHP, showing you how to use them effectively to automate tasks, browse data collections and create more dynamic programs.

The loops we will study in this chapter include:

- The while loop
- The do-while loop
- The for loop

We'll focus on the use, benefits and best practices for implementing each of these loops. You'll discover how these loops can be used to browse and manipulate data once you've studied them.

Get ready to dive into the captivating world of loops in PHP, where you'll learn how to manipulate the execution flow of your code in a precise and elegant way. By mastering loops, you'll be able to create more dynamic and powerful PHP applications. So, without further ado, let's explore the inner workings of PHP loops together!

### The while loop

The **while** loop is a control structure in PHP that allows you to execute a block of code repeatedly as long as a specified condition is true. It functions as follows:

- **Step 1:** Initialize condition: Before entering the **while** loop, a condition is defined. This condition is a Boolean expression that is evaluated before each iteration of the loop.
- **Step 2:** Condition evaluation: The condition is evaluated to determine whether it is true or false.
- **Step 3:** If the condition is true (i.e. returns true), the block of code inside the loop, i.e. the "Instructions" block, is executed. Once this block of code has been executed, the program returns to step 2 and re-evaluates the condition.
- **Step 4:** If the condition is false (i.e. returns false), the while loop ends and program execution continues after the loop.

![](img/caba2aa22f5409ba73dea47176330677_132_0.png)

To use the while loop effectively, it's essential to ensure that the specified condition will eventually become false at some point, otherwise you risk creating an infinite loop. You must also correctly update the variables used in the condition within the code block to ensure that the condition will eventually be false.

In short, the **while** loop allows you to execute a block of code repeatedly as long as a specified condition remains true. It's a powerful tool for creating flexible control structures in your PHP programs.

The basic syntax of the **while** loop is as follows:

```php
while (condition) {
// Block of code to execute while condition is true
}
```

Here's an example to illustrate the while loop:

```php
<?php
$counter = 1;

// Use the while loop to display numbers from 1 to 10
while ($counter <= 10) {
echo "The counter is: $counter <br>";
$counter++;
}
?>
```

In this code, we initialize a $counter variable to the value 1. Then we use a while loop to display the numbers from 1 to 10.

**Step 1:** Initialize the $counter variable to 1.

**Step 2:** The condition specified in the while loop is $counter <= 10. As long as this condition is true, the block of code inside the loop is executed.

**Step 3:** Each time the loop is iterated, the code inside the block is executed. In our case, we display the current counter value using echo. Then, at the end of each iteration, we increment the $counter value by 1 using the ++ operator. This ensures that the counter increases progressively with each iteration.

Repeat: Steps 2 to 3 are repeated as long as the condition $counter <= 10 remains true. Once $counter reaches 11, the condition becomes false and the while loop ends.

This code will display numbers from 1 to 10 using a while loop.

```
The counter is: 1
The counter is: 2
The counter is: 3
The counter is: 4
The counter is: 5
The counter is: 6
The counter is: 7
The counter is: 8
The counter is: 9
The counter is: 10
```

The while loop is extremely flexible and can be used in a variety of scenarios. It is particularly useful when you need to execute a block of code an indefinite number of times according to a condition.

### The do ... while loop

The do...while loop is similar to the while loop, but with one important difference: the condition is evaluated after the block of code has been executed. This means that the block of code is always executed at least once, even if the condition is false from the outset.

Here's how the do...while loop works:

- **Step 1:** First, the block of code (instruction) inside the loop is executed a first time without checking the condition.
- **Step 2:** Check condition: Once the block of code has been executed, the condition specified after the while keyword is evaluated.
- **Step 3:** If the condition is true, the block of code (instruction) is re-executed.
- **Step 4:** Otherwise, the loop ends

Repeat: Steps 1 to 3 are repeated as long as the condition specified after the **while** keyword remains true.
