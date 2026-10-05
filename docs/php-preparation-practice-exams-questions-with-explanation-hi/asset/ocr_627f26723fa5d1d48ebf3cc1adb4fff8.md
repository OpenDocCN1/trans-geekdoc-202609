Correct Answer: B

Explanation: The foreach loop is particularly powerful for iterating over associative arrays in PHP, as it automatically assigns both the key and the value to the specified variables during each iteration. This simplifies the code and makes it very readable when processing data stored in key-value pairs.

# Question 21. In a do...while loop in PHP, when does the loop body execute in relation to the condition being checked?

+   A. Before the condition is checked
B. After the condition is checked
C. Only when the condition is true
D. Only when the condition is false

Correct Answer: A

Explanation: In a do...while loop, the body of the loop executes first, and then the condition is evaluated. This guarantees that the loop body will run at least once, regardless of whether the condition evaluates to true or false initially. This is useful in scenarios where you want to ensure that a block of code executes before any condition is applied.

# Question 22. What is the significance of the break statement in a loop structure in PHP, particularly in the context of a switch statement?

+   A. It restarts the loop from the beginning.
B. It terminates the loop or switch statement immediately.
C. It pauses the loop for a specified duration.
D. It skips the current iteration of the loop.

Correct Answer: B

Explanation: The break statement serves to terminate the execution of a loop or a switch statement immediately. In a loop, it stops further iterations, while in a switch, it prevents fall-through to subsequent cases. This allows for more controlled execution flow, avoiding unintended behavior when multiple conditions are involved.