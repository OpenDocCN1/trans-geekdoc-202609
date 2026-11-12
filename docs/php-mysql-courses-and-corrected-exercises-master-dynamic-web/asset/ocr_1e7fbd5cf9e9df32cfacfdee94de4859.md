code moves on to the next statement.

The second if statement (nested in the else of the first) checks if $grade is greater than or equal to 16, which is true ($grade = 17), so this condition is satisfied and the message "Very good work!" is displayed.

In summary, nested control structures, such as those used in the previous examples, are effective for making decisions based on multiple conditions. However, as the number of conditions increases, the readability and maintainability of the code can quickly deteriorate. The complexity of nested control structures can make code difficult to understand and manage, increasing the risk of errors and making future modifications more laborious.

It's therefore important to pay close attention to the design and readability of your code, avoiding excessively nested control structures wherever possible. Whenever possible, it's best to use alternatives such as switch structures or functions to simplify the logic of your code and make it easier to understand and maintain.

# Multiple conditions

Multiple conditions, also known as combined conditions, allow us to evaluate several Boolean expressions in a single control statement. These conditions are generally used when we need to check several criteria simultaneously in order to make a decision.

The use of logical operators simplifies control structures by reducing the number of nested conditional blocks. This makes code easier to read and maintain.