Floor division (//) divides a numerator by a denominator, yielding the highest integer that's not greater than the result. Python truncates (discards) the fractional part:

```
In [5]: 7 // 4
Out[5]: 1

In [6]: 3 // 5
Out[6]: 0

In [7]: 14 // 7
Out[7]: 2
```

In true division, -13 divided by 4 gives -3.25:

```
In [8]: -13 / 4
Out[8]: -3.25
```

Floor division gives the closest integer that's not greater than -3.25—which is -4:

```
In [9]: -13 // 4
Out[9]: -4
```

# Exceptions and Tracebacks

Dividing by zero with / or // is not allowed and results in an exception—a sign that a problem occurred:

lick here to view code image

```
In [10]: 123 / 0
---------------------------------------------------------------------------
ZeroDivisionError                         Traceback (most recent call last)
ipython-input-10-cd759d3fcf39> in <module>()
----> 1 123 / 0

ZeroDivisionError: division by zero
```

Python reports an exception with a traceback. This traceback indicates that an excextion of type ZeroDivisionError occurred—most exception names end with Error. In interactive mode, the snippet number that caused the exception is specified