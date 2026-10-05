# D. method_exists()

Correct Answer: B

Explanation: is_callable() checks whether the contents of a variable can be called as a function. It is useful for determining a function, class method, or closure can be invoked, whereas function_exists() checks only if a function with a given name exists.

Question 52. In PHP, if an error occurs and you want to throw an exception instead of the default error handler, which function should you use to make this switch?

+   A. set_error_handler()
B. trigger_error()
C. throw_error()
D. set_exception_handler()

Correct Answer: A

Explanation: set_error_handler() is used to set a custom error handler in PHP. By using this function, you can handle errors in a user-defined way, such as throwing exceptions instead of using the default error-handling mechanism.

Question 53. Which of the following error types is NOT handled by the set_error_handler() function in PHP?

+   A. E_NOTICE
B. E_WARNING
C. E_PARSE
D. E_USER_NOTICE

Correct Answer: C

Explanation: The set_error_handler() function cannot handle E_PARSE errors because these are parsing errors that occur before the script is executed. Other error types, like E_NOTICE and E_WARNING, are handled during runtime.