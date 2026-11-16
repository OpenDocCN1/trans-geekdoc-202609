```
In [12]: ascending_letters
Out[12]: ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']

In [13]: letters
Out[13]: 'fadgchjebi'

In [14]: colors = ('red', 'orange', 'yellow', 'green', 'blue')

In [15]: ascending_colors = sorted(colors)

In [16]: ascending_colors
Out[16]: ['blue', 'green', 'orange', 'red', 'yellow']

In [17]: colors
Out[17]: ('red', 'orange', 'yellow', 'green', 'blue')
```

Use the optional keyword argument reverse with the value True to sort the elements in descending order.

# 5.9 SEARCHING SEQUENCES

Often, you'll want to determine whether a sequence (such as a list, tuple or string) contains a value that matches a particular key value. Searching is the process of locating a key.

# List Method index

List method index takes as an argument a search key—the value to locate in the list—then searches through the list from index o and returns the index of the first element that matches the search key:

lick here to view code image

```
In [1]: numbers = [3, 7, 1, 4, 2, 8, 5, 6]

In [2]: numbers.index(5)
Out[2]: 6
```

A ValueError occurs if the value you're searching for is not in the list.

# Specifying the Starting Index of a Search

Using method index's optional arguments, you can search a subset of a list's elements. You can use *= to multiply a sequence—that is, append a sequence to itself multiple