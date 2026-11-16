```
Out[4]: [2, 3, 5, 7, 11, 13]
```

# Specifying a Slice with Only a Starting Index

If you omit the ending index, Python assumes the sequence’s length (8 here), so snippet [5]’s slice contains the elements of numbers at indices 6 and 7:

lick here to view code image

```
In [5]: numbers[6:]
Out[5]: [17, 19]

In [6]: numbers[6:len(numbers)]
Out[6]: [17, 19]
```

# Specifying a Slice with No Indices

Omitting both the start and end indices copies the entire sequence:

lick here to view code image

```
In [7]: numbers[:]
Out[7]: [2, 3, 5, 7, 11, 13, 17, 19]
```

Though slices create new objects, slices make shallow copies of the elements—that is, they copy the elements’ references but not the objects they point to. So, in the snippet above, the new list’s elements refer to the same objects as the original list’s elements, rather than to separate copies. In the “Array-Oriented Programming with NumPy” chapter, we’ll explain deep copying, which actually copies the referenced objects themselves, and we’ll point out when deep copying is preferred.

# Slicing with Steps

The following code uses a step of 2 to create a slice with every other element of numbers:

```
In [8]: numbers[::2]
Out[8]: [2, 5, 11, 17]
```

We omitted the start and end indices, so 0 and len(numbers) are assumed, respectively.