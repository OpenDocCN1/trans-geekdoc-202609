```
TypeError
Traceback (most recent call last)
<ipython-input-15-812ef2514689> in <module>()
----> 1 s[0] = 'H'

TypeError: 'str' object does not support item assignment
```

# ttempting to Access a Nonexistent Element

Using an out-of-range list, tuple or string index causes an IndexError:

lick here to view code image

```
In [16]: c[100]
IndexError
Traceback (most recent call last)
ipython-input-16-9a31eale1a13> in <module>()
----> 1 c[100]

IndexError: list index out of range
```

# Using List Elements in Expressions

List elements may be used as variables in expressions:

```
In [17]: c[0] + c[1] + c[2]
Out[17]: -39
```

# Appending to a List with +=

Let's start with an empty list [], then use a for statement and += to append the values 1 through 5 to the list—the list grows dynamically to accommodate each item:

lick here to view code image

```
In [18]: a_list = []

In [19]: for number in range(1, 6):
    ...:     a_list += [number]
    ...:

In [20]: a_list
Out[20]: [1, 2, 3, 4, 5]
```