```
In [13]: another_value = int(input('Enter another integer: '))
Enter another integer: 13

In [14]: another_value
Out[14]: 13
```

Variables value and another_value now contain integers. Adding them produces an integer result (rather than concatenating them):

```
In [15]: value + another_value
Out[15]: 20
```

If the string passed to int cannot be converted to an integer, a ValueError occurs:

lick here to view code image

```
In [16]: bad_value = int(input('Enter another integer: '))
Enter another integer: hello
--------------------------------------------------------------------------------
ValueError                                 Traceback (most recent call last)
ipython-input-16-cd36e6cf8911> in <module>()
----> 1 bad_value = int(input('Enter another integer: '))

ValueError: invalid literal for int() with base 10: 'hello'
```

Function int also can convert a floating-point value to an integer:

```
In [17]: int(10.5)
Out[17]: 10
```

To convert strings to floating-point numbers, use the built-in float function.

# 2.7 DECISION MAKING: THE IF STATEMENT AND COMPARISON OPERATORS

A condition is a Boolean expression with the value True or False. The following determines whether 7 is greater than 4 and whether 7 is less than 4:

```
In [1]: 7 > 4
Out[1]: True
```