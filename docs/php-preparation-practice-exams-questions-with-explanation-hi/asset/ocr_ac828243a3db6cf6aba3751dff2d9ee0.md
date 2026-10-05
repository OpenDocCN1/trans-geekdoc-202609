Explanation: The == operator in PHP performs a loose comparison, meaning it checks if the values are equal after type juggling. Since both $a and $b evaluate to 5 when compared, the output of var_dump($a == $b); is bool(true). If a strict comparison (===) was used, it would return false due to differing types.

# Question 72. Which of the following is a valid way to create a constant in PHP?

+   A. const MY_CONSTANT = 100;
B. define("MY_CONSTANT", 100\);
C. constant MY_CONSTANT 100;
D. var MY_CONSTANT = 100;

Correct Answer: B

Explanation: The define() function is used to create constants in PHP, where the first argument is the name of the constant as a string and the second argument is its value. Option A is also valid in PHP 7.0 and later, but it is not universally applicable like define(). Options C and D use incorrect syntax for declaring constants.

# Question 73. How can you concatenate two strings in PHP?

+   A. $result = "Hello" + "World";
B. $result = "Hello" & "World";
C. $result = "Hello" . "World";
D. $result = "Hello" + "World";

Correct Answer: C

Explanation: In PHP, the dot operator (.) is used for string concatenation. Thus, $result = "Hello" . "World"; correctly concatenates the two strings. Options A and D use the addition operator which is not valid for string concatenation in PHP, and option B uses an incorrect operator.

# Question 74. Which of the following data types is not a built-in type in PHP?

+   A. String