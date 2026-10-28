# # How to code while and for statements

The while and for statements let you code loops that repeat a block of statements one or more times. This is illustrated by the statements in figure 2-16.

To code a *while statement*, you code the while keyword followed by a conditional expression in parentheses and a block of code in braces. When the while statement is executed, the conditional expression is evaluated. If the expression is TRUE, the block of code is executed and the *while loop* is tried again. As soon as the expression evaluates to FALSE, the block of code is skipped and the while statement is done. If the expression evaluates to FALSE the first time it is checked, the block of code won’t be executed at all.

The first example shows a loop that appends the numbers 1 through 5 to a variable named $message. Before the loop, a statement assigns a value of 1 to the $counter variable. Then, the while loop checks if the $counter variable is less than or equal to 5. If so, it executes the two statements in the loop.

Within the while loop, the first statement appends the counter and a pipe character ( | ) to the $message variable. Then, the second statement uses the increment operator (++) to increment the value in the $counter variable by 1. The loop ends when the value of $counter is greater than 5. As a result, when the while loop finishes, the $message variable contains a string value of “1|2|3|4|5|”.

To code a *for statement*, you code the for keyword followed by three statements in parentheses and a block of code in braces. The three statements are separated by semicolons. The first of these statements initializes the counter variable. It is executed just once. The second statement is a conditional expression that causes the code in the loop to be executed as long as it’s TRUE. The third statement increments the counter. It’s executed each time through the *for loop*, but after code in the loop is executed.

The second example shows how to get the same result as the first example with a for loop. Here, the $counter variable is initialized to 1; the loop is executed as long as $counter is less than or equal to 5; and $counter is incremented by 1 after each time through the loop. For a loop like this, a for statement is easier to use than a while statement.

The third example uses another while statement to calculate the future value of a one-time investment at a fixed interest rate. The first three variables store the investment amount, the yearly interest rate, and the number of years. The $future_value variable stores the value of the investment at the end of each year, and it’s initialized to the value of the investment amount.

Within the while statement, the variable named $i is used as the counter, so it is incremented by 1 each time through the loop. Within the loop, the year’s interest ($future_value * interest_rate) is added to the $future_value variable, and the result is stored back into the $future_value variable. When the loop finishes, the $future_value variable holds the future value of the investment.

The fourth example does the same calculation with a for loop. Here again, $i is used as the counter variable, which is a common programming practice. This name indicates that the variable stores an integer value. Since this variable is only used within the loop, there’s no need for a more descriptive name.