Python’s help function is especially useful for getting quick help on basic code elements, such as functions. For example, the use of Python’s abs function in Figure 1.2 might seem obvious to you, but if you’re not sure, you can learn more by entering help(abs), as shown in Figure 1.3.

![](bbox=[0.07, 0.2, 0.66, 0.34])

Figure 1.3
Getting help in the shell.
© 2014 Python Software Foundation.

# WORKING WITH NUMBERS

Almost all computer programs use numbers in some way or another. In this section, you explore arithmetic with two basic types of numbers in Python: integers and floating-point numbers. Along the way, the important concepts of variables, assignment, functions, and modules are introduced.

# Using Arithmetic

As you know from mathematics, integers are the infinite sequence of whole numbers {..., −2, −1, 0, 1, 2, ...}. Although this sequence is infinite in mathematics, in a computer program the sequence is finite and thus has a largest positive integer and a largest negative integer. In Python, the sequence of integers is quite large; the upper and lower bounds of the sequence depend on the amount of computer memory available.

Real numbers are numbers with a decimal point, such as 3.14 and 7.50. The digits to the right of the decimal point, called the fractional part, represent the precision of a real number. In mathematics, real numbers have infinite precision. The set of real numbers is also infinite. However, in a computer program, real numbers have an upper bound, a lower bound, and a finite precision (typically 16 digits). In Python and most other programming languages, real numbers are called floating-point numbers.

As you saw in the previous section, when you enter a number in the Python shell, Python simply displays that number; when you enter an arithmetic expression, Python evaluates and displays the value of that expression. Thus, the shell behaves like a pocket calculator