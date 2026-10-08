# Core PHP Programming

The conditional expression is evaluated to be either true or false. If true, the expression between the question mark and the colon is executed. Otherwise, the expression after the colon is executed. The following code fragment

```
($clientQueue > 0) ? serveClients() : cleanUp();
```

does the same thing as

```
if($clientQueue > 0)
    serveClients();
else
    cleanUp();
```

The similarity is deceiving. Although the abbreviated form seems to be equivalent to using if-else, at a deeper level it is not. As I said, ? is an operator, not a statement. This means that the expression as a whole will be evaluated. The value of the matched expression takes the place of the expression. In other words, something like

```
print(true ? "it's true" : "it's false");
```

is a valid statement. Since the conditional expression is true, the line will be transformed into

```
print("it's true");
```

which is something you can't do with an if statement.

The ? operator can be confusing to read and is never necessary. It wouldn't be bad if you never used it. On the other hand it allows you to write very compact code.

# The switch Statement

An alternative to if-else-else structures is the switch statement, which works on the assumption that you compare a single expression to a set of possible values. Figure 3-3 demonstrates the structure of the switch statement.