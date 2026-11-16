This is the equivalent of using +=. The following code adds all the characters of a string then all the elements of a tuple to a list:

lick here to view code image

```
In [8]: sample_list = []

In [9]: s = 'abc'

In [10]: sample_list.extend(s)

In [11]: sample_list
Out[11]: ['a', 'b', 'c']

In [12]: t = (1, 2, 3)

In [13]: sample_list.extend(t)

In [14]: sample_list
Out[14]: ['a', 'b', 'c', 1, 2, 3]
```

Rather than creating a temporary variable, like t, to store a tuple before appending it to a list, you might want to pass a tuple directly to extend. In this case, the tuple's parentheses are required, because extend expects one iterable argument:

lick here to view code image

```
In [15]: sample_list.extend((4, 5, 6)) # note the extra parentheses

In [16]: sample_list
Out[16]: ['a', 'b', 'c', 1, 2, 3, 4, 5, 6]
```

A TypeError occurs if you omit the required parentheses.

# Removing the First Occurrence of an Element in a List

Method remove deletes the first element with a specified value—a ValueError occurs if remove's argument is not in the list:

lick here to view code image

```
In [17]: color_names.remove('green')

In [18]: color_names
Out[18]: ['red', 'orange', 'yellow', 'blue', 'indigo', 'violet']
```