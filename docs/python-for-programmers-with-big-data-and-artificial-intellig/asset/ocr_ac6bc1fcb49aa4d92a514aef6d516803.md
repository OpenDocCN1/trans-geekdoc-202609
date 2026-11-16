lowercase or all uppercase letters. You also can change a string’s capitalization with methods capitalize and title.

# Capitalizing Only a String’s First Character

Method capitalize copies the original string and returns a new string with only the first letter capitalized (this is sometimes called sentence capitalization):

lick here to view code image

```
```
In [1]: 'happy birthday'.capitalize()
Out[1]: 'Happy birthday'
```
```

# Capitalizing the First Character of Every Word in a String

Method title copies the original string and returns a new string with only the first character of each word capitalized (this is sometimes called book-title capitalization):

lick here to view code image

```
```
In [2]: 'strings: a deeper look'.title()
Out[2]: 'Strings: A Deeper Look'
```
```

# 8.6 COMPARISON OPERATORS FOR STRINGS

Strings may be compared with the comparison operators. Recall that strings are compared based on their underlying integer numeric values. So uppercase letters compare as less than lowercase letters because uppercase letters have lower integer values. For example, 'A' is 65 and 'a' is 97. You’ve seen that you can check character codes with ord:

lick here to view code image

```
```
In [1]: print(f'A: {ord("A")}; a: {ord("a")}')
A: 65; a: 97
```
```

Let’s compare the strings 'Orange' and 'orange' using the comparison operators:

lick here to view code image

```
```
In [2]: 'Orange' == 'orange'
```
```