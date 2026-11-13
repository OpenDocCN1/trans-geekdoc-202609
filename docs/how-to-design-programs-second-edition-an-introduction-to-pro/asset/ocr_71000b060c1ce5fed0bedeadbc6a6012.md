```
(list (list 2 2 3 10)
 (list 0 3 9 21)
 (list 4 1 -2 1))
```

The goal of these subtractions is to put a 0 into the first column of all but the first equation. For the third equation, getting a 0 into the first position means subtracting the first equation twice from the third one:

```
(list (list 2 2 3 10)
 (list 0 3 9 21)
 (list 0 -3 -8 -19))
```

Following convention, we drop the leading 0’s from the last two equations:

```
(list (list 2 2 3 10)
 (list 3 9 21)
 (list -3 -8 -19))
```

That is, we first multiply each item in the first row with 2 and then subtract the result from the last row. As mentioned, these subtractions do not change the solution; that is, the solution of the original system is also the solution of the transformed one.

> Mathematics teaches how to prove such facts. We use them.

# **Exercise 464.** Check that the following system of equations

2 · x + 2 · y + 3 · z = 10
   3 · y + 9 · z = 21 (†)
 - 3 · y - 8 · z = -19

has the same solution as the one labeled with (†). Again do so by hand and with check-solution from exercise 462. ▪

**Exercise 465.** Design subtract. The function consumes two Equations of equal length. It “subtracts” a multiple of the second equation from the first, item by item, so that the resulting Equation has a 0 in the first position. Since the