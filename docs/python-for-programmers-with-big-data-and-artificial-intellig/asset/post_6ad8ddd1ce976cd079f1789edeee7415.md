
combinations of `False` and `True` values for `expression1` and `expression2`—such tables are called `truth tables`:

| expression1 | expression2 | expression1 and expression2 |
|---|---|---|
| False | False | False |
| False | True | False |
| True | False | False |
| True | True | True |

## Boolean Operator `or`

Use the **Boolean `or` operator** to test whether one _or_ both of two conditions are `True`. The following code tests a condition that’s `True` if either _or_ both simple conditions are `True`—the entire condition is `False` only if _both_ simple conditions are `False`:

Click here to view code image

```
In [4]: semester_average = 83

In [5]: final_exam = 95

In [6]: if semester_average >= 90 or final_exam >= 90:
    ...:     print('Student gets an A')
    ...:
Student gets an A
```

Snippet [6] also contains two simple conditions:

- `semester_average >= 90` determines whether a student’s average was an A (90 or above) during the semester, and
- `final_exam >= 90` determines whether a student's final-exam grade was an A.

The truth table below summarizes the Boolean or operator. Operator and has higher precedence than or.

| expression1 | expression2 | expression1 or expression2 |
|---|---|---|
| False | False | False |
| False | True | True |
| True | False | True |
| True | True | True |

## Improving Performance with Short-Circuit Evaluation

Python stops evaluating an `and` expression as soon as it knows whether the entire condition is `False`. Similarly, Python stops evaluating an `or` expression as soon as it knows whether the entire condition is `True`. This is called short-circuit evaluation. So the condition

Click here to view code image

```
gender == 'Female' and age >= 65
```

stops evaluating immediately if `gender` is not equal to `'Female'` because the entire expression must be `False`. If `gender` is equal to `'Female'`, execution continues, because the entire expression will be `True` if the age is greater than or equal to 65.

Similarly, the condition

Click here to view code image

```
semester_average >= 90 or final_exam >= 90
```

stops evaluating immediately if `semester_average` is greater than or equal to 90 because the entire expression must be `True`. If `semester_average` is less than 90, execution continues, because the expression could still be `True` if the `final_exam` is greater than or equal to 90.

In expressions that use `and`, make the condition that's more likely to be `False` the leftmost condition. In `or` operator expressions, make the condition that's more likely to be `True` the leftmost condition. These techniques can reduce a program's execution time.

## Boolean Operator `not`

The **Boolean operator `not`** “reverses” the meaning of a condition—`True` becomes `False` and `False` becomes `True`. This is a **unary operator**—it has only _one_ operand. You place the `not` operator before a condition to choose a path of execution if the original condition (without the `not` operator) is `False`, such as in the following code:

Click here to view code image

```
In [7]: grade = 87

In [8]: if not grade == -1:
    ...:     print('The next grade is', grade)
    ...:

The next grade is  87
```

Often, you can avoid using `not` by expressing the condition in a more “natural” or convenient manner. For example, the preceding `if` statement can also be written as follows:

Click here to view code image

```
In [9]: if grade != -1:
    ...:     print('The next grade is', grade)
    ...:

The next grade is  87
```

The truth table below summarizes the `not` operator.

| expression | not expression |
|---|---|
| False | True |
| True | False |

The following table shows the precedence and grouping of the operators introduced so far, from top to bottom, in decreasing order of precedence.

| Operators | Grouping |
|---|---|
| () | left to right |
| ** | right to left |
| * / // % | left to right |
| + - | left to right |
| < <= > >= == != | left to right |
| not | left to right |

## 3.14 INTRO TO DATA SCIENCE: MEASURES OF CENTRAL TENDENCY—MEAN, MEDIAN AND MODE

Here we continue our discussion of using statistics to analyze data with several additional descriptive statistics, including:

- **mean**—the *average value* in a set of values.
- **median**—the *middle value* when all the values are arranged in *sorted order*.
- **mode**—the *most frequently occurring value*.

These are **measures of central tendency**—each is a way of producing a single value that represents a “central” value in a set of values, i.e., a value which is in some sense typical of the others.

Let’s calculate the mean, median and mode on a list of integers. The following session creates a list called `grades`, then uses the built-in **sum** and `len` functions to calculate the mean “by hand”—`sum` calculates the total of the grades (397) and `len` returns the number of grades (5):

Click here to view code image

```
In [1]: grades = [85, 93, 45, 89, 85]

In [2]: sum(grades) / len(grades)
Out[2]: 79.4
```

The previous chapter mentioned the *descriptive statistics* count and sum—implemented in Python as the built-in functions `len` and `sum`. Like functions `min` and `max` (introduced in the preceding chapter), `sum` and `len` are both examples of functional-style programming **reductions**—they reduce a collection of values to a single value—the sum of those values and the number of values, respectively. In section .8's class-average example, we could have deleted lines 10–15 of the script and replaced `average` in line 16 with snippet [2]'s calculation.

The Python Standard Library's **statistics module** provides functions for calculating the mean, median and mode—these, too, are reductions. To use these capabilities, first `import` the `statistics` module:

```
In [3]: import statistics
```

Then, you can access the module’s functions with “statistics.” followed by the name of the function to call. The following calculates the `grades` list’s mean, median and mode, using the `statistics` module’s **mean**, **median** and **mode** functions:

Click here to view code image

```
In [4]: statistics.mean(grades)
Out[4]: 79.4

In [5]: statistics.median(grades)
Out[5]: 85

In [6]: statistics.mode(grades)
Out[6]: 85
```

Each function’s argument must be an **iterable**—in this case, the list `grades`. To confirm that the median and mode are correct, you can use the built-in **sorted function** to get a copy of `grades` with its values arranged in increasing order:

```
In [7]: sorted(grades)
Out[7]: [45, 85, 85, 89, 93]
```

The `grades` list has an odd number of values (5), so `median` returns the **middle value** (85). If the list’s number of values is even, `median` returns the **average** of the **two** middle values. Studying the sorted values, you can see that `85` is the mode because it occurs most frequently (twice). The `mode` function causes a `StatisticsError` for lists like

```
[85, 93, 45, 89, 85, 93]
```

in which there are two or more “most frequent” values. Such a set of values is said to be imodal. Here, both 85 and 93 occur twice.

## 3.15 WRAP-UP

In this chapter, we discussed Python’s control statements, including `if`, `if`…`else`, `if`…`elif`… `else`, `while`, `for`, `break` and `continue`. You saw that the `for` statement performs sequence-controlled iteration—it processes each item in an iterable, such as a range of integers, a string or a list. You used the built-in function `range` to generate sequences of integers from `0` up to, but not including, its argument, and to determine how many times a `for` statement iterates.

You used sentinel-controlled iteration with the `while` statement to create a loop that continues executing until a sentinel value is encountered. You used built-in function `range`’s two-argument version to generate sequences of integers from the first argument’s value up to, but not including, the second argument’s value. You also used the three-argument version in which the third argument indicated the step between integers in a range.

We introduced the `Decimal` type for precise monetary calculations and used it to calculate compound interest. You used f-strings and various format specifiers to create formatted output. We introduced the `break` and `continue` statements for altering the flow of control in loops. We discussed the Boolean operators `and`, `or` and `not` for creating conditions that combine simple conditions.

Finally, we continued our discussion of descriptive statistics by introducing measures of central tendency—mean, median and mode—and calculating them with functions from the Python Standard Library’s `statistics` module.

In the next chapter, you’ll create custom functions and use existing functions from Python’s `math` and `random` modules. We show several predefined functional programming reductions and you’ll see additional functional-programming capabilities.
