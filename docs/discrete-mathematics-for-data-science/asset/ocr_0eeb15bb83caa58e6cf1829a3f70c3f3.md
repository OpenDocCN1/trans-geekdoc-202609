```
{ f } f
```

Such a recursive function definition implies an unconditional self-reference, meaning that f is perpetually invoked. That could lead to errors and a waste of computing resources. Therefore, there should be conditions by which the function does not refer to itself, ceasing its operations. For example:

```
{ i + DUP 8 < f ?} f WORD
0 f (→ 8)
```

The function f will repeat only if the number on the top of the stack is less than 8. Therefore, the result of invoking the function f is that it calls itself 8 times, and the final solution of this particular function also happens to be 8.

The basis of a recursion may rest with the evaluation of a condition in an if-statement. In the above function f, the operator ? is an alias for IF. When given a true condition (1 is true and 0 is false), an if-statement allows a program to evaluate a specified expression or function. The pattern is:

*condition function evaluation*

Depending on the type of evaluation of a condition, such as =, >, or <, a function can be defined to repeat while the condition is true, signified by 1.

Suppose that we have a list of numbers ls and a function f that adds two numbers, given as:

```
{ 1 3 5 7 9 } ls LIST
{ + } f WORD
```