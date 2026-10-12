
# Chapter 6: Basic operation of Python Language

In the previous chapters, we have discussed various lexical concepts that are necessary to write efficient code. In this chapter, we will discuss various operations that made Python a popular language. This is a comprehensive chapter and introduces you to a lot of concepts in detail. Let us start!

## What is a statement?

When a variable is declared, an expression is used to create and process the object. If some logical control is added, a statement is formed. It can also be said that statements contain expressions, so statements are the most basic infrastructure for Python programs.

## Python Assignment Statement

Learning assignment statements in Python makes it easier to learn the other statements. Learning Python assignment statement is mainly to master and understand its logic.

### 1. Assignment statement

The essence of assignment statements in Python is to create a reference to an object. There are mainly the following methods of an assignment.

#### a) Basic assignment method

`first=5`

This is equivalent to creating a variable `first` that points to the object `5` stored in memory. `first=5` is an assignment statement. After performing the assignment operation, you can print or display the value of `first` at will.

#### 2) Understand assignment logic

When declaring variables, there are at least two parts, one is the variable table used to store variable names, and the other is the memory storage area [4,6]. When `first=5` is declared, the system first opens a storage space in the memory area, stores the value `5`, and then points the variable `first` to the object `5` stored in the memory, which is equivalent to having the object `5` first in the memory storage area. Then `first` appears in the variable table, and points to `5`. This point can also be called "reference".

Although the syntax of assignment statements is simple, please carefully understand the assignment logic in Python. This kind of assignment logic affects all aspects of Python. If you understand assignment logic, you can better understand and write Python programs. If you have programming experience in C language, you will know that variables in C programs hold value, while variables in Python point to a value. Variables exist only as a reference relationship and no longer have storage functions. In Python, each data occupies a memory space, and data is called an object in Python. An integer `5` is an `int` object, a `'hello'` is a string object, and a `[1, 2, 3]` is a list object. In Python, you can use the global built-in function `id(obj)` to obtain the id of an object as the storage address of the object in memory. The global built-in function is used directly and does not need to refer to any package.

> **Note:** The change of address before and after variable `first` indicates that the variable points to the object! After an object is created, it cannot be destroyed directly. Therefore, in the above example, the variable `a` points to the object `5` first, and then continues to execute `a=a+5`, which produces a new object `10`. Since the object `5` cannot be destroyed, let `A` point to the new object `10` instead of overwriting the object `5` with the object `10`. After the code execution is completed, there are still objects `5` and `10` in the memory, but the variable `A` points to the new object `10`. If no variable points to object `5` (it cannot be referenced), Python will use a garbage collection mechanism to decide whether to recycle it (this is automatic and does not require the programmer to worry about it). There is a garbage collection mechanism inside Python. The garbage collection mechanism detects that if no variable references an object within a specific time, the object will be collected, releasing the resources it occupies. There is a reference counter inside Python, and the garbage collection mechanism judges whether an object has a reference according to the reference counter, to decide whether to automatically release the resources occupied by the object. The garbage collection mechanism targets unreferenced objects in Python and is inferred from a result obtained by a reference counter. This understanding is also very important. When we talk about data types such as lists in the future, we will see again the importance of correctly understanding the variable pointing to the object.

### Multi-objective assignment

The multi-objective assignment is a way of assigning the same value to multiple variables.

### Enhanced assignment or parameterized assignment

Sometimes it is desirable to replace the original value of a variable by re-assigning it after doing an operation based on its original value.

### Exchange the values of two variables

In other languages, such as Java, C, C++, etc., at least three lines of code are required to exchange the values of two variables, while in Python, only one line of code is required to exchange the values of two variables.

Before introducing other Python statements, let us look at the sequential execution and basic input and output in Python process control. Sequential execution is the default code execution method in process control and is relatively simple. The basic principle is that the sequence of code execution is consistent with the sequence of program code writing. The program execution order is consistent with the writing order. The data in the above program is fixed in the program, but sometimes it may be necessary for programmers or software users to input some data into the program during the operation of the program, which requires input functions.

## `input()` function

Input on the console is realized through the global function `input()`. The `input()` function receives information input from the console by the user. The default type is a `str` character type, which can be converted into specific data types as required. If you want to give the user some hints when inputting data, you can pass in a parameter with hints in the `input()` function!

## `eval()` function

The `eval()` function evaluates `str` character data as a valid expression and returns the result. Simply put, it is to remove the quotation marks at the left and right ends of the string.

## `print()` function

The `print()` function here simply outputs the value of an object or variable. The `print()` function has some commonly used parameters, which are very flexible to use in actual development. If you want to use a special line of characters to separate the output of the front and back lines, such as 20 "=" to separate the output of the front and back lines, you can use `print("="*20)` to achieve the goal.

### 1) Multiple variables are output on one line, separated by spaces by default

Outputs multiple contents separated by commas on one line, with the separator being a space.

### 2) Multiple variables are output on one line, and the separator between them is changed

If you want the output to be separated by other separators, you can write a delimiter statement. Any character can be used as the delimiter here, that is, the `print()` function can specify the delimiter manually.

### Multiple lines of `print()` function output on one line

In the parameter table of the `print()` function, there is a parameter `end` that specifies the termination symbol. by default, it is a line break, that is, `end='\n'`. Therefore, the output of multiple print statements can be output on one line by specifying a terminator.

The default delimiter for the `print()` function is a space, and the terminating symbol is a newline `\n`. After understanding the above contents, the flexibility of output will be greatly improved in actual development.

## Digital print format

Specify the format or number of digits of the output number by formatting the string.

### 1) Outputs decimals of specified digits

In the print format, the `:` in curly brackets indicates that the value appearing at the current position is formatted, and the `.2f` indicates that the following value is output as floating-point, but only 2 decimal places are reserved, and the third digit is rounded.

### 2) output a fixed width value

If you want to specify the width of the overall digital output, the form is as follows: `width {Enter value}`

> **Note:** `{:12, .2f}` means the total width, which is aligned to the right by default, with not enough digits, and is preceded by a space; `,` means thousands separator; `.2f` means keeping 2 decimal places.

Because sometimes it is necessary to output multiple lines of content on the console, and each line has multiple columns, but each line has a length and a short length. If you want to typeset more neatly, you can use this method at this time. For more usage of the `print()` function, please refer to it through the `help(print)` command.

With this, we have completed a comprehensive chapter that explained to us a lot of python programming concepts. In the next chapter, we will in detail discuss modules that give interactivity to python. Let us go!
