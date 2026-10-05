# Fundamentals of the q Programming Language

# Join

The symbol , is used to join two lists:

```
(@ 1 2 3 4), (5 6 7 8 9)
```

The join operator can join lists of any type:

```
(@ 1 2 3 4), `a, "hello"
```

```
((@ 1 2 3 4);;"hello")
```

# Print to console

The symbol ! has important functionalities which will be reviewed later. The particular function involving ! ! is:

```
ØN3
```

which prints the argument on the right-hand side to console in an unformatted form but also allows q to use the argument further down the statement for subsequent operations on the left. In particular, when using the q prompt, we can use ØN! as control prints:

```
1+ØN!1 +ØN!1+ØN!
```

+   1
2
3
4

This is useful to track the evaluation of a complicated statement – such functionality, however, does not work when using IDEs.

# Separator

We saw that the symbol ; denotes the end of a statement. However, when surrounded by brackets, it acts as a separator for elements within a list:

```
(1;2;3;4)
```

1 2 3 4