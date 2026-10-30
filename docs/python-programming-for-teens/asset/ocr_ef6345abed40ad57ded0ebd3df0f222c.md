```
False
>>> "44".isnumeric()
True
>>> "Ken Lambert".index('L')
4
>>> "Ken Lambert".split()
['Ken', 'Lambert']
```

You should be able to tell what these operations do just by examining the results. But if you’re unsure of any of them, ask for help by entering help(str.methodName) in the shell.

# WORKING WITH LISTS

People make and use lists of things for many different purposes, such as playlists of music or wish lists for shopping. In programming, you can create and process lists of numbers, strings, or any other data values. In this section, you explore the use of lists in Python.

# List Literals and Operators

A list is a sequence of data values called items. Items can be any data values whatsoever. Like the characters in a string, the items in a list are ordered by position, counting from 0. In Python, a list literal is represented as a sequence of items separated by commas. The sequence of items is enclosed in square brackets, as shown in the next shell session.

```
>>> [34, 46, 22]
[34, 46, 22]
>>> emptyList = []
>>> len(emptyList)
0
>>> item1 = 34
>>> item2 = "Ken"
>>> listOfTwoItems = [item1, item2]
>>> listOfTwoItems
[34, 'Ken']
>>> listOfLists = [listOfTwoItems, emptyList]
>>> listOfLists
[[34, 'Ken'], []]
```

Note the following points about these lists:

+   - The empty list, [], contains no items and has a length of 0.
+   - Lists can contain other data structures, such as strings and lists.