
### Question 22
Which Python data type is mutable?
A. `Tuple`
B. `String`
C. `List`
D. `Integer`

### Question 23
What is the correct way to assign a value to a variable in Python?
A. `variable = 10`
B. `10 = variable`
C. `var <- 10`
D. `variable : 10`

### Question 24
Which Python library is commonly used for data analysis?
A. NumPy
B. TensorFlow
C. Pandas
D. All of the above

### Question 25
What is a key benefit of Jupyter Notebook for Python programming?
A. It is a lightweight text editor
B. It supports interactive coding with visual output
C. It eliminates the need for Python installation
D. It is only used for debugging

# 2.12 Answers to Chapter Review Questions
1. B. Readability and simplicity
Explanation: Python is widely known for its simple and human-readable syntax, making it easy to learn and use.
2. D. Assembly Programming
Explanation: Python supports Object-Oriented, Functional, and Procedural Programming but not Assembly Programming, which is a low-level language.
3. B. Rich ecosystem of libraries like Pandas and NumPy
Explanation: Python's popularity in data science is due to its extensive libraries like Pandas and NumPy, which simplify data manipulation and analysis.
4. B. Jupyter Notebook
Explanation: Jupyter Notebook is a popular tool in data science workflows, offering interactive coding and visualization capabilities.
5. B. To isolate project dependencies
Explanation: Python virtual environments allow projects to manage their own dependencies independently, avoiding conflicts between packages.
6. B. PyCharm
Explanation: PyCharm is an IDE specifically designed for Python development, offering features like code completion and debugging.
7. A. Configure the Python SDK
Explanation: Configuring the Python SDK is the first step when setting up Python in IntelliJ IDEA to enable Python project development.
8. B. `_variable`
Explanation: Variable names in Python must not start with numbers, cannot include special characters like `@`, and use underscores instead of hyphens.
9. A. `<class 'float'>`
Explanation: The `type()` function returns the type of the value, and `42.0` is a floating-point number.
10. B. `type()`
Explanation: The `type()` function in Python is used to check the type of a variable or value.
11. C. Accepts data from the user as a string
Explanation: The `input()` function takes input from the user and returns it as a string.
12. B. `print("Hello, World!")`
Explanation: In Python, the `print()` function is used to display output, and the correct syntax includes parentheses.
13. B. `str.format()`
Explanation: The `str.format()` method is a flexible way to format strings in Python.
14. B. `"r"`
Explanation: The `"r"` mode is used to open a file for reading in Python.
15. D. All of the above
Explanation: Python supports multiple data types, including `Integer`, `String`, and `List`.
16. B. Converting one data type to another
Explanation: Type conversion in Python refers to changing a value from one data type to another, such as from string to integer.
17. C. Typing code into a web browser
Explanation: Python programs can run in the terminal, IDEs, or notebooks, but not directly in a web browser unless using specific platforms.
18. B. To correct errors and ensure proper program execution
Explanation: Debugging helps identify and fix issues in the code, ensuring it runs as expected.
19. B. Avoid comments for clarity
Explanation: Best practices encourage the use of comments to clarify code, making it easier for others and yourself to understand later.
20. C. String
Explanation: The `input()` function always returns the user input as a string by default, even if the input is a number.
21. A. Using the `venv` module
Explanation: The `venv` module is the recommended way to create virtual environments in Python.
22. C. List
Explanation: Lists are mutable, meaning their elements can be modified after creation, unlike tuples and strings.
23. A. `variable = 10`
Explanation: Variables in Python are assigned values using the `=` operator.
24. D. All of the above
Explanation: NumPy, TensorFlow, and Pandas are commonly used Python libraries for data analysis and related tasks.
25. B. It supports interactive coding with visual output
Explanation: Jupyter Notebook allows interactive coding, real-time visualization, and inline documentation, making it a powerful tool for Python programming.

# Chapter 3. Python Fundamentals for Data Science
Python is a fundamental programming language for Data Science due to its simplicity, versatility, and extensive libraries. This chapter covers essential Python concepts, starting with control flow, including loops, conditionals, and loop control statements, which help manage program execution efficiently. It then explores functions and modules, highlighting their importance in structuring reusable code. The chapter also delves into Python’s core data structures—lists, tuples, dictionaries, and sets—comparing their use cases to help select the right one for different tasks. Finally, it introduces file handling, explaining how to read, write, and manage files, including binary operations, exception handling, and best practices. Mastering these Python fundamentals provides a strong foundation for working with data in real-world applications.

## 3.1 Control Flow: Loops and Conditionals
Control flow in Python allows you to dictate the execution order of your code based on conditions or repetitive tasks. Two primary components of control flow are conditionals and loops. They help in decision-making and executing repetitive tasks efficiently.

### 3.1.1 Conditionals in Python
Conditionals enable your program to execute specific blocks of code based on whether a condition is True or False.

#### if, elif, and else Statements
- `if`: Executes a block of code if a specified condition is True.
- `elif`: Specifies additional conditions if the previous ones are False.
- `else`: Executes a block of code if all preceding conditions are False.

Syntax:
```
if condition1:
    # Code block 1
elif condition2:
    # Code block 2
else:
    # Code block 3
```
Example:
```
age = 18
if age < 18:
    print("You are a minor.")
elif age == 18:
    print("You just became an adult.")
else:
    print("You are an adult.")
```
Output:
You just became an adult.

#### Nested Conditionals
Conditionals can be nested within each other to evaluate more complex scenarios.
```
score = 85
if score >= 50:
    if score >= 90:
        print("Excellent!")
    else:
        print("Good job!")
else:
    print("Better luck next time!")
```

### 3.1.2 Loops in Python
Loops are used to execute a block of code repeatedly, either for a specified number of times or until a condition is met.

#### for Loop
Used to iterate over a sequence e.g., list, tuple, dictionary, string, or range.

Syntax:
```
for variable in sequence:
    # Code block
```
Example:
```
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```
Output:
apple
banana
cherry

#### range() in for Loops
The `range()` function generates a sequence of numbers.
```
for i in range(5):  # 0, 1, 2, 3, 4
    print(i)
```
Example with Start and Step:
```
for i in range(1, 10, 2):  # Start=1, End=10, Step=2
    print(i)
```
Output:
1
3
5
7
9

#### while Loop
Executes a block of code as long as a condition is True.

Syntax:
```
while condition:
    # Code block
```
Example:
```
count = 0
while count < 5:
    print(count)
    count += 1
```
Output:
0
1
2
3
4

#### Infinite Loops
Be cautious of conditions that never become False, as they lead to infinite loops:
```
# Warning: This creates an infinite loop!
while True:
    print("This will run forever.")
```

### 3.1.3 Loop Control Statements
Loop control statements alter the flow of loops, allowing you to skip iterations or terminate the loop entirely.

#### break Statement
Terminates the loop and moves to the next statement after the loop.

Example:
```
for num in range(10):
    if num == 5:
        break
    print(num)
```
Output:
0
1
2
3
4
