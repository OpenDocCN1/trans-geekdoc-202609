In this example, the conditional expression that the loop uses to determine whether or not to iterate once more is simply ‘1’. As this expression is always 1, it always evaluates to true and therefore the loop will continue for ever, or until the server forces a stop.

# 9.4 The ‘do-while’ loop construct

The ‘do-while’ loop is similar to the ‘while’ loop. The difference is where and when the loop expression is checked. In a ‘while’ loop, we have shown that the loop expression is checked at the start of the loop. Therefore, if the expression is false at the start, none of the statements within the loop are executed. With a ‘do-while’ loop the expression is evaluated at the end of the loop, after the statements within the loop have been executed at least once.

The syntax of the loop is:

```
do
    statement
while ( expression );
```

Figure 9.13 illustrates the syntax of the ‘do-while’ loop.

Like the other flow-of-control constructs previously, braces can be used to group multiple statements to be executed within the loop:

```
do {
    statement
    statement
    ...
}
while ( expression );
```

![](bbox=[0.155, 0.69, 0.725, 0.937])