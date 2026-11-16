```
In [7]: 1000 in numbers
Out[7]: False

In [8]: 5 in numbers
Out[8]: True
```

Similarly, operator `not in` tests whether its right operand's iterable does _not_ contain the left operand's value:

```
In [9]: 1000 not in numbers
Out[9]: True

In [10]: 5 not in numbers
Out[10]: False
```

# Using Operator `in` to Prevent a `ValueError`

You can use the operator `in` to ensure that calls to method `index` do not result in `ValueError`s for search keys that are not in the corresponding sequence:

lick here to view code image

```
In [11]: key = 1000

In [12]: if key in numbers:
    ....:     print(f'found {key}   at index {numbers.index(search_key)}')
    ....: else:
    ....:     print(f'{key} not found')
    ....:

1000 not found
```

# Built-In Functions `any` and `all`

Sometimes you simply need to know whether _any_ item in an iterable is `True` or whether _all_ the items are `True`. The built-in function `any` returns `True` if any item in its iterable argument is `True`. The built-in function `all` returns `True` if all items in its iterable argument are `True`. Recall that nonzero values are `True` and 0 is `False`. Non-empty iterable objects also evaluate to `True`, whereas any empty iterable evaluates to `False`. Functions `any` and `all` are additional examples of internal iteration in functional-style programming.