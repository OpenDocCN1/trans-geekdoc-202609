# A Python 2.7 Programming Tutorial 185

```
[0, 1, 2, 3, 4, 5]
>>> L[2]
2
>>> L[4]
4
>>> L[2:4]
[2, 3]
>>> s = 'abcde'
>>> s[2]
'c'
>>> s[4]
'e'
>>> s[2:4]
'cd'
```

Note in the example above that the elements are selected from position 2 to position 4, which does not include the element L[4].

You may omit the starting position to slice elements from the beginning of the sequence to the specified position. You may omit the ending position to specify a slice that extends to the end of the sequence. You may even omit both in order to get a copy of the whole sequence.

```
>>> L[:4]
[0, 1, 2, 3]
>>> L[4:]
[4, 5]
>>> L[:]
```

You can replace part of a list by using a slicing expression on the left-hand side of the "=" in an assignment statement, and providing a list of replacement elements on the right-hand side of the "=". The elements selected by the slice are deleted and replaced by the elements from the right-hand side.

In slice assignment, it is not necessary that the number of replacement elements is the same as the number of replaced elements. In this example,