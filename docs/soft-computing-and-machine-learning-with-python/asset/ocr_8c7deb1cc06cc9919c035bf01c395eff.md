# Soft Computing Machine Learning with Python

s.ljust(n)

For any string expression s, this method returns a new string containing the characters from s with enough spaces added after it to make a new string of length n.

```
>>> "Ni".ljust(4)
'Ni  '
>>> "Too long to fit".ljust(4)
'Too long to fit'
```

Note that the .ljust() method will never return a shorter string. If the length isn't enough, it just returns the original value.

There is a similar method that right-justifies a string value:

s.rjust(n)

This method returns a string with enough spaces added before the value to make a string of length n. As with the .rjust() method, it will never return a string shorter than the original.

```
>>> "Ni".rjust(4)
'  Ni'
>>> m = "floccinaucinihilipilification"
>>> m.rjust(4)
'floccinaucinihilipilification'
```

# .strip(), .lstrip(), and .rstrip(): Remove Leading and/or Trailing Whitespace

Sometimes you want to remove whitespace (spaces, tabs, and newlines) from a string. For a string s, use these methods to remove leading and trailing whitespace:

+   - s.strip() returns s with any leading or trailing characters removed.
- s.lstrip() removes only leading whitespace.
- s.rstrip() removes only trailing whitespace.

```
>>> spaceCase = '\n \t Moon \t\t ''
>>> spaceCase
'
 \t Moon \t\t '
```