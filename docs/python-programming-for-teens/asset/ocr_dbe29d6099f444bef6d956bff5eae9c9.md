appropriate names and arguments for these functions and let them worry about how they do their jobs. In other words, passing the buck and procrastination are virtues!

+   - You continue to pass the buck at each level of the design. To complete each function, you think of other functions to call, with the appropriate arguments.
+   - The buck appears to stop when you call a built-in function.
+   - Although there is occasionally some overlap, the subtasks in a top-down design are typically different from each other and thus call for different functions to perform them.

Recursive design shares some of these characteristics with top-down design but also differs in important ways, as you will see in the next subsection.

# Recursive Function Design

In recursive design, a problem is broken into subproblems of the same form. In these cases, you assign each subproblem to the same function as the one that solves the problem at a higher level. A function of this sort is called a recursive function.

For example, consider the problem of computing the summation of a sequence of integers from a lower bound to an upper bound. The function summation(1, 4) should return the result of 1 + 2 + 3 + 4, or 10. One way to design a solution to this problem is to recognize that this sequence of additions contains the following nested summations:

```
summation(1, 4) = 1 + summation(2, 4)
summation(2, 4) = 2 + summation(3, 4)
summation(3, 4) = 3 + summation(4, 4)
summation(4, 4) = 4
```

Note that the last case, summation(4, 4), is not composed of another summation but simply returns one if its arguments. Figure 7.2 shows a call diagram for summation(1, 4).

![](bbox=[0.07, 0.7, 0.7, 0.9])

Figure 7.2
A call diagram of summation(1, 4).