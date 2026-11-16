```
In [11]: set()
Out[11]: set()
```

Python displays an empty set as `set()` to avoid confusion with Python’s string representation of an empty dictionary (`{}`).

# Frozenset: An Immutable Set Type

Sets are *mutable*—you can add and remove elements, but set *elements* must be *immutable*. Therefore, a set cannot have other sets as elements. A **frozenset** is an *immutable* set—it cannot be modified after you create it, so a set *can* contain frozensets as elements. The built-in function `frozenset` creates a frozenset from any iterable.

# 6.3.1 Comparing Sets

Various operators and methods can be used to compare sets. The following sets contain the same values, so == returns `True` and != returns `False`.

lick here to view code image

```
In [1]: {1, 3, 5} == {3, 5, 1}
Out[1]: True

In [2]: {1, 3, 5} != {3, 5, 1}
Out[2]: False
```

The `<` operator tests whether the set to its left is a **proper subset** of the one to its right—that is, all the elements in the left operand are in the right operand, and the sets are not equal:

lick here to view code image

```
In [3]: {1, 3, 5} < {3, 5, 1}
Out[3]: False

In [4]: {1, 3, 5} < {7, 3, 5, 1}
Out[4]: True
```

The `<=` operator tests whether the set to its left is an **improper subset** of the one to its right—that is, all the elements in the left operand are in the right operand, and the sets might be equal: