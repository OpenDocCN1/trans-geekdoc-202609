# 28

# LANGUAGE FUNDAMENTALS

or nested lists:

+   (1;2;(1;2);4

+   1
2
1 2
4

As we will see in the next chapter, the symbol ; also separates arguments when defining a function. Finally – as we saw previously – it separates statements:

```
a:1;b:2;a+b
```

+   3

We may easily write quite complicated commands within one line. If a separator is used to separate statements, the statements are evaluated one by one from the left, but within a statement, the right-to-left priority is used. q does not consider the end of a line (newline operator) as the end of a statement so one statement can also be written in multiple lines for better clarity. For reducing clutter in our code, we should also keep separate statements in separate lines.

# Quit

The symbol \ is not a symbol per se but plays an important role. When entered in the q session, it will terminate the session.

# Index

The “at” sign, @, is known as “apply” and can be used to apply a monadic (one-argument) function to its argument. Since q is a functional language, indexing is a function, too, and we can use index to apply a vector to a list of indices. The following forms are equivalent:

```
max [1 2 3]
max 1 2 3
max# 2 3
```

```
x:1 2 3
x[0 1]
x @0 1
x@@0 1
```