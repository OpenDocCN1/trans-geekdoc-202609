
Negative numbers are represented with a minus sign. This sign is also used to negate more complex expressions, as in - (3 * 5). The precedence of the minus sign when used in this way is higher than that of any other arithmetic operator.

Table 1.2 shows the precedence of the arithmetic operators, where the operators of higher precedence are evaluated first.

### Table 1.2 The Precedence of Arithmetic Operators

| Operator | Precedence |
|---|---|
| - (unary negation) | 4 |
| ** | 3 |
| *, /, //, % | 2 |
| +, - (binary subtraction) | 1 |

The exponentiation operator ** is also right associative. This means that consecutive ** operators are evaluated from right to left. Thus, the expression 2 ** 3 ** 2 produces 512, whereas (2 ** 3) ** 2 produces 64.

Finally, a note on style: although Python ignores spaces within arithmetic expressions, the use of spaces around each operator can make your code easy for you and other people to read. For example, compare

```
34+67*2**6-3
```

to

```
34 + 67 * 2 ** 6 - 3
```

## Working with Variables and Assignment

Suppose you are working on a program that computes and uses the volume of a sphere. You are given the sphere’s radius of 4.2 inches. You first compute its volume using the formula 4/3πr³, with 3.1416 as your estimate of π. Here is the Python expression you might write for that:

```
4 / 3 * 3.1416 * 4.2 ** 3
```

If the value of this expression is used just once in your program, you compute it just once and use it there. However, if it is used in several places in your program, you must write the same expression several times. That’s a waste of your time in writing code and a waste of the computer’s time in evaluating it. Is there a way to write the expression, compute its value just once, and then simply use this value many times thereafter?

Yes, there is, and that’s one reason why programs use variables. A variable in Python is a name that stands for a value. A Python variable is given a value by using the assignment operator =, according to the following form:

```
variable = expression
```

where variable is any Python name (with a few exceptions to be discussed later) and expression is any Python expression (including the arithmetic expressions under discussion here). Thus, in our example, the variable volume could be given the volume of the sphere via the assignment

```
volume = 4 / 3 * 3.1416 * 4.2 ** 3
```

and then used many times in other code later on. Note that because the precedence of assignment is lower than that of the other operators, the expression to the right of the = operator is evaluated first, before the variable to the left receives the value.

Now, suppose you had to compute the volumes of several different spheres. You could type out the expressions 4 / 3 and 3.1416 every time you write the code to compute a new volume. But you could instead use other variables, such as FOUR_THIRDS and PI, to make these values easy to remember each time you repeat the formula. Figure 1.4 shows a session in the shell where these values are established and the volumes of two spheres, with radii 4.2 and 5.4, are computed.

![](img/4dc3f6307b32ff815a6d58ec1c84708c_35_0.png)

Figure 1.4
Using variables in code fragments.
© 2014 Python Software Foundation.

Python variables are spelled using letters, digits, and the underscore (`_`). The following rules apply to their use:

- A variable must begin with a letter or an underscore (`_`) and contain at least one letter.
- Variables are case sensitive. Thus, the variable `volume` is different from the variable `Volume`, although they may refer to the same value.
- Python programmers typically spell variables in lowercase letters but use capital letters or underscores to emphasize embedded words, as in `firstVolume` or `first_volume`.
- When the value of a variable will not change after its initial assignment, it's considered a constant. PI is an example of a constant. Python programmers typically spell constants using all caps to indicate this.
- Before you can use a variable, you must assign it a value. An attempt to use a variable that has not been initialized in this way generates an error message, as shown in Figure 1.5.

![](img/4dc3f6307b32ff815a6d58ec1c84708c_36_0.png)

Figure 1.5
Attempting to use a variable that has not been assigned a value.
© 2014 Python Software Foundation.

To summarize, there are three reasons to use variables in Python code:

- 1. They make code easy to read and understand.
- 2. They help to eliminate unnecessary computations.
- 3. They make code easy to modify and maintain (to be discussed later).

## Using Functions

As you have seen, the arithmetic and assignment operations consist of an operator and one or more operands. Python also provides many other basic operations, which are packaged as functions. A function is like an operator but is referred to by a name rather than an operator symbol. When a function is evaluated or called, its operands are supplied to it in the form of arguments. For example, the Python function abs expects a number as its single argument and computes and returns that number’s absolute value. Thus, the function call abs(-34) returns 34.

When a Python function is called, Python first evaluates its arguments. The resulting values are then passed to the function, which uses them to compute and return its value. Although the written form of a function call is slightly different, the process is no different from evaluating an expression with operands and operators. The form of a function call is as follows:

```
functionName(argumentExpression1, argumentExpression2, ...)
```

Function calls are expressions, and their arguments are expressions. For example, the arithmetic expression

```
abs(length - width) + 2
```

produces a result, as long as the variables length and width refer to numbers.

Some Python functions allow for optional arguments as well as required arguments. For example, the Python function round expects one required argument: the number to be rounded. If that number is a floating-point number, the integer value nearest to it is returned. However, round can also be called with a second argument: an integer indicating the number of places of precision to use in the result. Thus, round(3.1416) returns 3, whereas round(3.1416, 3) returns 3.142.

Generally, the number of arguments used with a function must match the number of its required arguments, unless it allows optional arguments. For functions provided by Python, the types of the arguments (such as numbers) used must also match the types of the arguments expected at each position in the sequence of arguments.

## Using the math Module

Python’s functions either are already available to call in the shell or must be imported from modules before use. A Python module is just a library of functions and other resources. There are many such modules, as you can see by browsing the modules index

in the Python documentation. One of these is the `math` module, which contains useful functions for operations on numbers.

There are several ways to import a function from a module to make it available for use. The most common way is to use the form

```
import moduleName
```

where *moduleName* is the name of the module. When you have done this, you can call any function in the module by using the form

```
moduleName.functionName(sequenceOfArguments)
```

For example, suppose you want to compute the square root of 2. The following shell session shows how to do this:

```
>>> import math
>>> math.sqrt(2)
1.4142135623730951
```

Alternatively, if you prefer not to use the module name as a prefix in a function call, you can explicitly import the desired function, as follows:

```
>>> from math import sqrt
>>> sqrt(2)
1.4142135623730951
```

To view all the functions available in the `math` module, you run `dir(math)` after importing math, as follows:

```
>>> import math
>>> dir(math)
['__doc__', '__file__', '__loader__', '__name__', '__package__', 'acos', 'acosh', 'asin',
'asinh', 'atan', 'atan2', 'atanh', 'ceil', 'copysign', 'cos', 'cosh', 'degrees', 'e',
'erf', 'erfc', 'exp', 'expm1', 'fabs', 'factorial', 'floor', 'fmod', 'frexp', 'fsum',
'gamma', 'hypot', 'isinf', 'isfinite', 'isnan', 'ldexp', 'lgamma', 'log', 'log10',
'log1p', 'log2', 'modf', 'pi', 'pow', 'radians', 'sin', 'sinh', 'sqrt', 'tan', 'tanh',
 'trunc']
```

If you have studied trigonometry, you should be able to spot the trigonometric functions, such as `cos` and `sin`, in this list. Note also that the variable `pi`, which is Python’s name for the constant PI, is present. The value of this variable is Python’s most precise estimate of π.
