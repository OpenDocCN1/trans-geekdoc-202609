# 3.4 PROTECTED-catch

The concept of try-, or protected evaluation, is implemented with same verbs as the apply functions covered previously. The trap function has the syntax `f;arg;err` where f is a monadic function and arg its argument `[g;arg;err]` when g is a multivalent function and args its argument list. The expression err is executed if the evaluation of f or g fails.

Let us consider an example:

```
f:@[sqrt;x;`err`]
```

The function f executes the square root of variable x. If it fails, the symbol `err` is returned. Let us see a number of examples:

| f 9f |
|---|
| 3f |
| f -3f |
| 0n |
| f "Q" |
| 9f |
| as the ASCII of "Q" is 81, and, finally |
| ` a |
| `err |

> Further, the example of a protected evaluation for dyadic functions reads:
mult:{.*(x;y);`err`}

where the function mult multiplies x and y. If the multiplication fails, the symbol `err` is returned. Namely:

| mult[4;5] |
|---|
| 20 |
| mult[4;"toto"]] |
| `err |