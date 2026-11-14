```
def mean (* pair):
    sum = 0
    for elem in pair:
        sum = sum + elem
    return sum / len (pair)
print (average (3, 4))
print (average (10.2, 14, 12, 9.5, 13.4, 8, 9.2))
print (average (2))
```

```
>>>
3.5
10.9
2.0
```

The function calculates the average value of the sequence of numbers that is sent as an argument to the input parameter, which expects to receive a tuple. The function can be improved to avoid dividing by 0, in case of entering an empty tuple.

# Tuple Methods

As in the strings, there are methods associated with tuple type objects and lists. but only the methods: s.index (x) and s.count (x). You can also use the internal functions max and min when the tuples (or lists) are of numerical values. If the elements are strings, calculate the major or minor element, according to the position in the ASCII table of the first character. Let’s see some examples,

```
a = (2, 3, 4, 5, 79, -8, 5, -4)
>>> a.index (5) # index of the first occurrence of 5 in a
3
>>> a.count (5) # total occurrences of 5 in a
2
```