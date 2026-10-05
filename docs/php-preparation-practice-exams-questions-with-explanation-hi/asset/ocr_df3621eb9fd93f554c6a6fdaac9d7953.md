B. function checkNumber($number) { if ($number < 0) return "Negative number not allowed."; }

C. function checkNumber($number) { if ($number < 0) throw new Exception("Negative number not allowed."); }

D. function checkNumber($number) { if ($number < 0) die("Negative number not allowed."); }

Correct Answer: A

Explanation: The correct answer is A because it correctly throws an InvalidArgumentException when a negative number is passed. If this exception is not caught, it will result in a fatal error, terminating the script and displaying the error message specified. Option C is also valid but does not specify the type of exception as InvalidArgumentException.

# Question 94. When using the try-catch block in PHP, what happens if an exception is thrown inside the block and there is no corresponding catch block to handle it?

+   A. The script will continue executing normally, and the exception will be logged.

+   B. The script will halt execution immediately, and a fatal error will be displayed.

+   C. The script will terminate, and the error message will be sent to the browser.

+   D. The script will enter an infinite loop due to the unhandled exception.

Correct Answer: C

Explanation: The correct answer is C, as when an exception is thrown in a block and is not caught, it results in a fatal error, terminating the script. The error message associated with the exception is displayed to the browser, making crucial to ensure that exceptions are properly handled to avoid such behavior.

# Question 95. What is the difference between a regular function and a closure in PHP, particularly regarding the scope of variables and the ability to access variables from the parent scope?