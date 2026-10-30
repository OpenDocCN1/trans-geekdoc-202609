# Boolean Values

Named for the nineteenth century British mathematician and logician George Boole, a Boolean expression returns one of two values: `True` or `False`. These values are taken to mean “yes” or “no” when they result from evaluating Boolean expressions. Like the words for, from, and import, the words `True` and `False` are Python *keywords*. They are colored orange in IDLE and cannot be used as the names of variables. Like the numbers and other literals, the values `True` and `False` evaluate to themselves.

# Comparisons

The == operator compares any two Python values for equality and returns `True` if they’re equal and `False` if they’re not. The != operator stands for “not equal to” and returns the opposite results of ==. Here are some example comparisons:

```
>>> 34 == 0
False
>>> 34 != 0
True
>>> 34 == 2 * 17
True
>>> "Ken" == "KEN"
False
>>> "Ken" == 34
False
```

As you can see, comparisons are Boolean expressions. Note that Python compares two strings by examining the pairs of characters at each position. Because "e" does not equal "E", the strings "Ken" and "KEN" are not equal.

The operators <, >, <=, and >= are used to compare values that can be ordered in ascending or descending order. Thus, you can compare two numbers or two strings in this manner. You should try these other comparison operators in the shell to make sure you understand their meanings.

# Logical Operations

Boole used the values `True` and `False` in a system of logic. There are three basic operations in this system:

+   - **Logical negation**—This operation applies the logical operator `not` to a Boolean expression. The result returned is `False` if the expression is `True` and `True` if the expression is `False`.