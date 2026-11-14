unlike tuples, its elements can be modified, eliminated or increased. The
elements of the lists can be simple data (numerical or Boolean), strings, tuples or
other lists. Elements are indexed the same as tuples and string, through an
integer. The syntax of the lists is a sequence of comma-separated values
enclosed in square brackets. Examples:

```
>>> v1 = [2, 4, 6, 8, 10]
>>> type (v1)
<class 'list'>
>>> v2 = [7, 8.5, 'a', 'Hello', (2, 3), [11, 12]]
>>> v2
[7, 8, 'a', 'Hello', (2, 3), [11, 12]]
>>> games = ['tennis', 'baseball', 'football', 'voleyball', 'swimming']
>>> games
['tennis', 'baseball', 'football', 'voleyball', 'swimming']
```

The v1 list consists of integers, while v2 includes integers, reals, strings, tuples
and a list as its last element. The variable games refer to a list object with 5
elements of type string. It is similar to the previously defined tuple, but its
elements can be modifiable. It is a dynamic structure.

We can generate a list with a sequence of integers with the data type range (), of
the form,

```
>>> v = list (range (1,11))
>>> v
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

In Python versions 2.x, range () is a function that directly generates a list.
However, in versions 3.x, being range () a type of data range, we have to convert
it to a list with the function list (). This function also serves to convert iterable
data types, such as strings or tuples to list type. You can also create an empty
list. Examples:

```
>>> t = (1, 2, 3)
>>> list (t)
[1, 2, 3]
```