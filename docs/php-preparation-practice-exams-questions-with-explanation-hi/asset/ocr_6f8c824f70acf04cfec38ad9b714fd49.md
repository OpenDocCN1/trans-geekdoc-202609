# Question 54. In PHP, what will happen if you call a non-existing function and do not handle it using a custom function handler or exception?

+   A. PHP will silently ignore the call.
B. PHP will throw an uncaught exception.
C. PHP will trigger a fatal error.
D. PHP will output a warning message.

Correct Answer: C

Explanation: When you call a non-existing function in PHP and do not handle it, PHP will trigger a fatal error, which will stop the script execution. To manage such situations, you could use function_exists() or custom error handling.

# Question 55. If you want to ensure that a resource is properly cleaned up, like closing a file or database connection, regardless of whether an exception occurs, which PHP feature should you use?

+   A. try-finally block
B. try-catch block
C. try-catch-finally block
D. throw statement

Correct Answer: C

Explanation: The try-catch-finally block ensures that the finally part always runs, whether or not an exception is thrown. It is ideal for resource cleanup, ensuring the code in the finally block executes after the try or catch blocks, even if exceptions occur.

# Question 56. In PHP, which error reporting function allows you to control which types of errors and warnings are displayed during script execution?

+   A. error_log()
B. error_reporting()
C. set_error_handler()
D. trigger_error()