argument, so s. split () can be used to separate words in a text. The resulting substring (words, in this case) are returned in a list with the substring as elements.

# Examples

We will show a couple of examples of travel or search in a string to (i) count the number of ‘to’, (ii) the number of the given character or sub-string ‘c1’ and search for a character or substring.

```
```python
def count (s):
    """ "Count letter a in a string
>>> countLetter ('hot potato', 'a')
1
>>> countLetter ('Esplugues', 'a')
0
""" "
    n = 0
    for c in s:
        if c == 'a':
            n = n + 1
    return n
```
```

# Option with s.count () method

```
```python
def count (s):
    return s.count ('a')
```
```

```
```python
def count (s, c1):
    """ "Count letter or sub-string c1 in string s
    Examples:
    >>> count ('hot potato', 'a')
    1
    >>> count ('potato', 'u')
```
```