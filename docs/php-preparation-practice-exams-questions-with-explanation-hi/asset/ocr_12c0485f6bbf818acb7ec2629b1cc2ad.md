Question 23. In PHP, when is it necessary to use curly braces {} in control structures like if, for, and while?

+   A. Curly braces are never necessary.

+   B. They are required only if there are multiple statements to execute.

+   C. They are only needed in loops, not if in statements.

+   D. They must always enclose the entire block of code, regardless of the number of statements.

Correct Answer: B

Explanation: In PHP, curly braces are required to define the block of code associated with control structures like if, for, and while when there are multiple statements to execute. However, if there is only a single statement, they can be omitted, which can lead to more concise code. Nevertheless, using braces is generally recommended for clarity and to avoid mistakes in the future.

Question 24. Which of the following PHP constructs is specifically designed to execute a block of code repeatedly as long as a specified condition evaluates to true, allowing the execution of the code to continue until the condition becomes false, potentially making it a preferred choice for scenarios where the number of iterations is not known beforehand?

+   A. for

+   B. foreach

+   C. switch

Correct Answer: C

Explanation: The while loop is used in PHP to repeatedly execute a block of code as long as a specified condition is true. This is particularly useful when the number of iterations is not predetermined, as allows for dynamic execution based on runtime conditions. Unlike for and foreach, which require predefined bounds or data structures, the while loop evaluates the condition before each iteration, ensuring that it runs only as long as necessary.