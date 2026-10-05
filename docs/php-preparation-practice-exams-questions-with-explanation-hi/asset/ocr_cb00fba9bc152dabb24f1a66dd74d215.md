comparison, so 10 == "10" evaluates to true. The strict equality operator (===) would yield a different result.

# **Question 88.** Which of the following statements is true regarding PHP arrays?

+   A. Arrays can only contain integer keys.
B. Arrays can only contain string values.
C. Arrays can hold values of different types.
D. Arrays are immutable in PHP.

Correct Answer: C

Explanation: In PHP, arrays can hold values of different types, meaning they can mix integers, floats, and even other arrays within the same array. Options A and B are incorrect because PHP arrays support both string and integer keys, as well as various data types for values. Option D is incorrect as PHP arrays are mutable, allowing modifications.

# **Question 89.** Which of the following is the correct way to concatenate two strings in PHP?

+   A. string1 + string2;
B. string1 . string2;
C. string1 & string2;
D. string1 concat string2;

Correct Answer: B

Explanation: In PHP, the dot operator (.) is used for string concatenation. string1 . string2 correctly combines the two strings. Options A and D incorrectly suggest using operators that are not valid for string concatenation in PHP, while C uses an incorrect operator.

# **Question 90.** What is the primary method in PHP to include the contents of one file into another file during the execution of a script, and what are the implications of using this method concerning variable scope?

+   A. include