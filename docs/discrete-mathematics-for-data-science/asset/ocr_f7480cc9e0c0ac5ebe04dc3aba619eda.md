to a function pointer in C). For example, we can store a mini program on the data stack such as:

```
4 5 + ' 7 8 - '
```

We can then run that stored program from the data stack with the following instructions:

```
{ EXEC >> } 2 LREPEAT
-1
9
```

The “>>” operator rotates the value on the top of the stack to the bottom of the stack, allowing LREPEAT to execute all of the operations on the data stack.

There is special handling of in-line expressions containing tick words. For example, the following four expressions each give the same result of 8:

```
3 5 + '
3 5 { + ' } LE
3 5 + '
+ ' 3 5 GSC i- MOVE
```

Note that “LE” executes a lambda expression and “GSC i-MOVE” moves 2nd value from the bottom of the data stack to the top, where GSC provide the count of items on the data stack.