
whereas the while loop checks the condition before each iteration, potentially skipping execution if the condition is false initially.

## **Question 93.** When utilizing the continue statement within a loop in PHP, what effect does it have on the execution flow of the loop?

- A. It terminates the entire loop immediately.
- B. It skips the remaining code in the current iteration and proceeds to the next iteration.
- C. It restarts the loop from the beginning.
- D. It causes an infinite loop.

Correct Answer: B

Explanation: The continue statement in PHP is used within loops to skip the rest of the code in the current iteration and continue with the next iteration. This can be useful for skipping certain conditions while still allowing the loop to execute for other values, controlling the flow of the loop effectively.

## **Question 94.** What will be the output of a conditional structure where a variable holds a value of 5 and is checked against several conditions to see if it is greater than 10, greater than 5, or less than or equal to 5?

- A. Greater than ten
- B. Greater than five
- C. Five or less
- D. No output

Correct Answer: C

Explanation: The conditional structure evaluates the variable in order. Since the variable holds the value of 5, it does not meet the first two conditions. Therefore, the default outcome is executed, which indicates that the variable is "Five or less".

## **Question 95.** What will be the result when using a switch statement to check the value of a variable that equals 18 against different age categories including 16, 18, and 21?

- A. You are a teenager.
- B. You can vote.
- C. You are an adult.
- D. Age not categorized.

Correct Answer: B

Explanation: In the switch statement, the value of the variable is compared to each case. Since it equals 18, the second case is matched, resulting in the output "You can vote". The switch statement then breaks, preventing any further evaluation.

## **Question 96.** If a score is evaluated in a series of conditional statements to assign a grade, and the score is 85, which grade will be assigned?

- A. Grade: A
- B. Grade: B
- C. Grade: C
- D. Grade: D

Correct Answer: B

Explanation: The score of 85 satisfies the condition for Grade B, as it is greater than or equal to 80 but less than 90. The other conditions for A, C, and D do not apply, making "Grade: B" the final output.

## **Question 97.** What is the output when a day variable is set to "Monday" in a switch statement that categorizes days as either weekend or weekday?

- A. It's the weekend!
- B. It's a weekday.
- C. Invalid day.
- D. No output.

Correct Answer: B

Explanation: The switch statement checks the value of the day. Since "Monday" is a weekday, it falls into the case that outputs "It's a weekday."

## **Question 98.** What happens when if-else structure checks a variable for a negative number and the variable holds a positive value?

- A. It will print a positive message.
- B. It will execute the negative block.
- C. It will execute the else block.
- D. No action will be taken.

Correct Answer: C

Explanation: When if-else structure checks a variable with a positive value, the condition evaluates as false. Consequently, else block executes, which typically handles the case of non-negative.

## **Question 99.** In a nested if-else structure that checks for even number and then checks if that number is greater than 10, what would happen if the number is 4?

- A. Even and greater than ten.
- B. Even but not greater ten.
- C. Not even.
- D. No conditions met.

Correct Answer: B

Explanation: The outer condition identifies the number as even, but the inner condition fails since 4 is not greater than 10. Therefore, the outcome is "Even but not greater ten".

## **Question 100.** What will be the result of PHP script that checks multiple conditions to determine if a number is either zero, positive, or negative, when the number is set to -3?

- A. The number is zero.
- B. The number is positive.
- C. The number is negative.
- D. The number is undefined.

Correct Answer: C

Explanation: The control structure evaluates the number and identifies it as negative. Since it meets the condition for negativity, the output declares "The number is negative".

# CHAPTER 3 MCQs

## Functions and Error Handling

## **Question 1.** What is the correct way to define function in PHP that takes an argument by reference?

- A. function(&$arg)
- B. function(&arg)
- C. function($arg)

Correct Answer: A

Explanation: In PHP, to pass a function argument by reference, you must place an ampersand (&) before the parameter name in the function definition, like &$arg. This allows the function to modify the variable's value outside its scope.

## **Question 2.** Which error level is used to handle fatal runtime errors in PHP?

- A. E_NOTICE
- B. E_WARNING
- C. E_ERROR
- D. E_PARSE

Correct Answer: C

Explanation: E_ERROR represents fatal runtime errors that halt the script execution. Unlike warnings or notices, the script cannot continue after a fatal error. This error level is used for unrecoverable errors.

## **Question 3.** What does the set_error_handler() function do in PHP?

- A. It sets a user-defined function to handle errors.
- B. It suppresses all errors in the script.
- C. It logs errors to a specified file.
- D. It terminates the script upon encountering an error.

Correct Answer: A

Explanation: The set_error_handler() function allows developers to define a custom function that will be called whenever an error occurs. This user-defined function PHP handles the error and performs custom actions, such as logging or displaying specific error messages.

## **Question 4.** In PHP, how can you catch multiple exceptions in the same try-catch block?

- A. By using separate try blocks for each exception.
- B. By chaining multiple catch blocks after the try block.
- C. By using the catch(Exception $e) statement for all exceptions.
- D. By using a finally block for handling all exceptions.

Correct Answer: B

Explanation: PHP allows you to catch multiple exceptions by chaining multiple catch blocks after a try block. Each catch block can handle a different type of exception. This approach provides a structured way to handle different errors in the same context.

## **Question 5.** How do you handle an uncaught exception in PHP to avoid a fatal error?

- A. Use the throw keyword directly in your code.
- B. Use the trigger_error() function.
- C. Use the set_exception_handler() function.
- D. Use @ tap to suppress the error.

Correct Answer: C

Explanation: The set_exception_handler() function is used to define a custom function to handle any uncaught exceptions. This function will be called when an exception is thrown but not caught, allowing the script to handle the error gracefully without terminating.

## **Question 6.** In PHP, how can you pass a function's arguments by reference so that changes made to the arguments within the function are reflected outside the function as well? Assume a function that needs to modify the values of the arguments passed into it.

- A. Prefix the function arguments with the & symbol inside the function definition.
- B. Prefix the function arguments with the & symbol inside the function call.
- C. Use the global keyword inside the function to modify external variables.
- D. Declare the function with the var keyword to allow passing by reference.

Correct Answer: A

Explanation: Prefixing the argument with the & symbol in the function definition allows passing by reference, allowing the function to modify the original variable. The other options either refer to incorrect approaches or concepts not related to passing by reference in PHP.

## Question 7. What happens in PHP when a function is called without a required parameter that has no default value? Consider a function that is defined as test($param) and then called as test().

- A. PHP throws TypeError and terminates script execution.
- B. PHP throws a Warning and assigns a NULL value to the missing parameter.
- C. PHP throws a Fatal error and stops script execution.
- D. PHP assigns the default value of NULL to the missing parameter and continues executing.

Correct Answer: C

Explanation: If a required parameter is missing in a function call, PHP throws a Fatal error, halting the script's execution. Only parameters with default values or optional parameters can be omitted in function calls without causing an error.

## Question 8. What is the correct way to handle exceptions in PHP when working with a function that may throw an exception? Assume you have a function that throws an exception under certain conditions, and you need to catch and handle this exception.

- A. Use the try-catch block to catch exceptions thrown by the function.
- B. Use the throw keyword inside the function call to manually throw the exception.
- C. Use the error_reporting function to suppress exceptions.
