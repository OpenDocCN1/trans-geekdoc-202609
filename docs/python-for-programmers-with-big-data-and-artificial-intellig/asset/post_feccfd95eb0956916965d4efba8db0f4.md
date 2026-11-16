
Click here to view code image

```
Class average is 81.7
```

Lines 5–6 create the variables `total` and `grade_counter` and initialize each to 0.
Line 7

Click here to view code image

```
grades = [98, 76, 71, 87, 83, 90, 57, 79, 82, 94] # list of 10 grades
```

creates the variable `grades` and initializes it with a list of 10 integer grades.

The `for` statement processes each `grade` in the list `grades`. Line 11 adds the current `grade` to the `total`. Then, line 12 adds `1` to the variable `grade_counter` to keep track of the number of grades processed so far. Iteration terminates when all 10 grades in the list have been processed. The *Style Guide for Python Code* recommends placing a blank line above and below each control statement (as in lines 8 and 13). When the `for` statement terminates, line 15 calculates the average and line 16 displays it. Later in this chapter, we use functional-style programming to calculate the average of a list's items more concisely.

## Introduction to Formatted Strings

Line 16 uses the following simple f-string (short for **formatted string**) to format this script's result by inserting the value of `average` into a string:

Click here to view code image

```
f'Class average is {average}'
```

The letter `f` before the string's opening quote indicates it's an f-string. You specify where to insert values by using *placeholders* delimited by curly braces (`{` and `}`). The placeholder

```
{average}
```

converts the variable `average`'s value to a string representation, then replaces {average} with that **replacement text**. Replacement-text expressions may contain values, variables or other expressions, such as calculations or function calls. In line 16, we could have used `total / grade_counter` in place of `average`, eliminating the need for line 15.

## 3.9 SENTINEL-CONTROLLED ITERATION

Let’s generalize the class-average problem. Consider the following requirements statement:

> Develop a class-averaging program that processes an arbitrary number of grades each time the program executes.

The requirements statement does not state what the grades are or how many there are, so we’re going to have the user enter the grades. The program processes an arbitrary number of grades. The user enters grades one at a time until all the grades have been entered, then enters a *sentinel value* (also called a *signal value*, a *dummy value* or a *flag value*) to indicate that there are no more grades.

### Implementing Sentinel-Controlled Iteration

The following script solves the class average problem with sentinel-controlled iteration. Notice that we test for the possibility of division by zero. If undetected, this would cause a fatal logic error. In the “Files and Exceptions” chapter, we write programs that recognize such exceptions and take appropriate actions.

Click here to view code image

```
1 # class_average_sentinel.py
2 """Class average program with sentinel-controlled iteration."""
3
4 # initialization phase
5 total = 0 # sum of grades
6 grade_counter = 0 # number of grades entered
7
8 # processing phase
9 grade = int(input('Enter grade, -1 to end: ')) # get one grade
10
11 while grade != -1:
12     total += grade
13     grade_counter += 1
14     grade = int(input('Enter grade, -1 to end: '))
15
16 # termination phase
17 if grade_counter != 0:
18     average = total / grade_counter
19     print(f'Class average is {average:.2f}')
20 else:
21     print('No grades were entered')
```

Click here to view code image

```
Enter grade, -1 to end: 97
Enter grade, -1 to end: 88
Enter grade, -1 to end: 72
Enter grade, -1 to end: -1
Class average is 85.67
```

### Program Logic for Sentinel-Controlled Iteration

In sentinel-controlled iteration, the program reads the first value (line 9) before reaching the while statement. The value input in line 9 determines whether the program’s flow of control should enter the while’s suite (lines 12–14). If the condition in line 11 is False, the user entered the sentinel value (-1), so the suite does not execute because the user did not enter any grades. If the condition is True, the suite executes, adding the grade value to the total and incrementing the grade_counter.

Next, line 14 inputs another grade from the user and the condition (line 11) is tested again, using the most recent grade entered by the user. The value of grade is always input immediately before the program tests the while condition, so we can determine whether the value just input is the sentinel before processing that value as a grade.

When the sentinel value is input, the loop terminates, and the program does not add -1 to total. In a sentinel-controlled loop that performs user input, any prompts (lines 9 and 14) should remind the user of the sentinel value.

### Formatting the Class Average with Two Decimal Places

This example formatted the class average with two digits to the right of the decimal point. In an f-string, you can optionally follow a replacement-text expression with a colon (:) and a format specifier that describes how to format the replacement text. The format specifier .2f (line 19) formats the average as a floating-point number (f) with two digits to the right of the decimal point (.2). In this example, the sum of the grades was 257, which, when divided by 3, yields 85.66666666.... Formatting the average with .2f rounds it to the hundredths position, producing the replacement text 85.67. An average with only one digit to the right of the decimal point would be formatted with a **trailing zero** (e.g., 85.50). The chapter “Strings: A Deeper Look” discusses many more string-formatting features.

## 3.10 BUILT-IN FUNCTION RANGE: A DEEPER LOOK

Function `range` also has two- and three-argument versions. As you’ve seen, `range`’s one-argument version produces a sequence of consecutive integers from 0 up to, but not including, the argument’s value. Function `range`’s two-argument version produces a sequence of consecutive integers from its first argument’s value up to, but not including, the second argument’s value, as in:

Click here to view code image

```
In [1]: for number in range(5, 10):
    ...:     print(number, end=' ')
    ...:
5 6 7 8 9
```

Function `range`’s three-argument version produces a sequence of integers from its first argument’s value up to, but not including, the second argument’s value, *incrementing* by the third argument’s value, which is known as the **step**:

Click here to view code image

```
In [2]: for number in range(0, 10, 2):
    ...:     print(number, end=' ')
    ...:
0 2 4 6 8
```

If the third argument is negative, the sequence progresses from the first argument’s value *down* to, but not including the second argument’s value, *decrementing* by the third argument’s value, as in:

Click here to view code image

```
In [3]: for number in range(10, 0, -2):
    ...:     print(number, end=' ')
    ...:
10 8 6 4 2
```

## 3.11 USING TYPE DECIMAL FOR MONETARY AMOUNTS

In this section, we introduce Decimal capabilities for precise monetary calculations. If you’re in banking or other fields that require “to-the-penny” accuracy, you should investigate Decimal’s capabilities in depth.

For most scientific and other mathematical applications that use numbers with decimal points, Python’s built-in floating-point numbers work well. For example, when we speak of a “normal” body temperature of 98.6, we do not need to be precise to a large number of digits. When we view the temperature on a thermometer and read it as 98.6, the actual value may be 98.5999473210643. The point here is that calling this number 98.6 is adequate for most body-temperature applications.

Floating-point values are stored in binary format (we introduced binary in the first chapter and discuss it in depth in the online “Number Systems” appendix). Some floating-point values are represented only approximately when they’re converted to binary. For example, consider the variable amount with the dollars-and-cents value 112.31. If you display amount, it appears to have the exact value you assigned to it:

```
In [1]: amount = 112.31

In [2]: print(amount)
112.31
```

However, if you print amount with 20 digits of precision to the right of the decimal point, you can see that the actual floating-point value in memory is not exactly 112.31 —it’s only an approximation:

Click here to view code image

```
In [3]: print(f'{amount:.20f}')
112.31000000000000227374
```

Many applications require precise representation of numbers with decimal points. Institutions like banks that deal with millions or even billions of transactions per day have to tie out their transactions “to the penny.” Floating-point numbers can represent some but not all monetary amounts with to-the-penny precision.

The Python Standard Library 1 provides many predefined capabilities you can use in your Python code to avoid “reinventing the wheel.” For monetary calculations and other applications that require precise representation and manipulation of numbers
