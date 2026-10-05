This is particularly useful for filtering conditions within loops, allowing certain iterations to be bypassed based on specific criteria.

# **Question 14.** When using an if statement in PHP, which of the following correctly illustrates how to handle multiple conditions that can lead to the same outcome?

+   A. Only one if statement is needed.

+   B. Each condition must be evaluated separately with its own if.

+   C. Use multiple if statements.

+   D. Use logical operators within a single statement.

Correct Answer: D

Explanation: Utilizing logical operators (like && && AND, || for OR) within a single statement allows multiple conditions to be evaluated together, simplifying the control structure. This makes the code cleaner and more efficient, as multiple statements can be cumbersome and less readable.

# **Question 15.** In PHP, when using a switch statement, what will happen if none of the case statements match the value being evaluated and there is no default case defined?

+   A. The program will terminate with an error.

+   B. The code will execute the first case statement.

+   C. The code will skip the switch block entirely without executing any code.

+   D. The switch block will execute all case statements sequentially.

Correct Answer: C

Explanation: When none of the case statements match the evaluated expression and there is no default case provided, the switch statement will not execute any of its associated code blocks. This behavior allows for clean control flow without unintended consequences, as it prevents running any code when the condition is not met.

# **Question 16.** What is the primary purpose of using the continue statement within a loop in PHP?