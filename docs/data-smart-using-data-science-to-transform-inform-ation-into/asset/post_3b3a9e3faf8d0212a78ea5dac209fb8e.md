
![](img/9c4b3d77873bec9e7da149a75c568d36_167_0.png)

Figure 5.31: The LP formulation for the first split

But wait. There’s more!

One of the problems with using a “Big M” constraint is that Solver often has trouble confirming it’s actually found the optimal solution. So it’ll just sit there and spin its wheels even though it’s got a great solution in its back pocket. To prevent that from happening, click the Options button in Solver and set the Max Subproblems value to 15,000. That ensures that Solver quits after about 20 minutes on my laptop.

Go ahead and click Solve—regardless of whether you’re using Solver or OpenSolver (see the sidebar) when the algorithm terminates because of a user-defined limit, it may tell you that while it found a feasible solution, it didn’t solve to optimality. This just means that the algorithm didn’t prove optimality (similar to how nonlinear solvers are unable to prove optimality), but in this case, your solution should be strong nonetheless.

Once you have a solution, the Split1 tab should appear as in Figure 5.32.

| Customers | Community | Score | UB1 | UB2 | Total Score |
|---|---|---|---|---|---|
| Adams | 1 | 6.135 | 6.135 | 14.000 | 0.464 |
| Allen | 0 | 2.371 | 9.238 | 2.371 | |
| Anderson | 0 | 7.303 | 14.303 | 7.303 | |
| Bailey | 1 | 7.450 | 7.450 | 16.406 | |
| Baker | 0 | 2.932 | 10.317 | 2.932 | |
| Barnes | 0 | 3.371 | 8.084 | 3.371 | |
| Bell | 0 | 7.303 | 14.303 | 7.303 | |
| Bennett | 1 | 6.573 | 6.573 | 15.105 | |
| Brooks | 0 | 1.494 | 13.238 | 1.494 | |
| Brown | 1 | 6.573 | 6.573 | 14.371 | |
| Butler | 0 | 1.124 | 2.807 | 1.124 | |
| Campbell | 0 | 5.618 | 11.632 | 5.618 | |
| Carter | 1 | 7.012 | 7.012 | 14.695 | |

Figure 5.32: Optimal solution for the first split

## LIMITS ON DECISION VARIABLE

Some versions of Excel place limits on the number of decision variables you’re allowed to use with Solver. If you’re using a premium version of Solver, this is likely not an issue. However, for most home versions of Office 365, this problem is too big for solver. If Solver doesn't start to optimize but instead reports you have too many decision variables, you’ll want to use OpenSolver. For OpenSolver, set up the problem with regular Solver. Before solving, open the OpenSolver Model options on the Insert tab. OpenSolver has the same difficulty with “Big M” constraints, so before running the model, click the OpenSolver options button from inside the Model dropdown and set the time limit to 300 seconds. If you don’t do this, the default runtime on OpenSolver is really high. It’ll run for a long time if you let it.

My Solver run came up with 0.464 for the modularity; your solution may be better if you use OpenSolver. Running down column B, you can see who ended up in community 0 and who ended up in community 1. The question then is, are you done? Are there only two communities or are there more? To answer that question, you need to try to split up these two communities.

## Split 2: Electric Boogaloo

All right. Split up these communities like you’re doing cell division. You start by making a copy of the Split1 tab and calling it Split2. The first thing you need to do is insert a new column after the community values in column B. Label this new column C Last Run and copy the values over from B into C. This gives the sheet pictured in Figure 5.33.

| | A | B | C | D | E | F | G | H | I |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Customers | Community | Last Run | Score | UB1 | UB2 | | Total Score | |
| 2 | Adams | 1 | 1 | 6.135 | 6.135 | 14.000 | | 0.464 | |
| 3 | Allen | 0 | 0 | 2.371 | 9.238 | 2.371 | | | |
| 4 | Anderson | 0 | 0 | 7.303 | 14.303 | 7.303 | | | |
| 5 | Bailey | 1 | 1 | 7.450 | 7.450 | 16.406 | | | |
| 6 | Baker | 0 | 0 | 2.932 | 10.317 | 2.932 | | | |
| 7 | Barnes | 0 | 0 | 3.371 | 8.084 | 3.371 | | | |
| 8 | Bell | 0 | 0 | 7.303 | 14.303 | 7.303 | | | |
| 9 | Bennett | 1 | 1 | 6.573 | 6.573 | 15.105 | | | |
| 10 | Brooks | 0 | 0 | 1.494 | 13.238 | 1.494 | | | |
| 11 | Brown | 1 | 1 | 6.573 | 6.573 | 14.371 | | | |
| 12 | Butler | 0 | 0 | 1.124 | 2.807 | 1.124 | | | |
| 13 | Campbell | 0 | 0 | 5.618 | 11.632 | 5.618 | | | |
| 14 | Carter | 1 | 1 | 7.012 | 7.012 | 14.695 | |

Figure 5.33: The Split2 tab with previous run values

In this model, the decisions are the same—customers are given a 1 or a 0. But you need to keep in mind that if two customers are given 1s this time around, they're not necessarily in the same community. If one of them was in community 0 on the first run and the other was in community 1, they're in two different communities.

In other words, the only scores Adams might get for being in, say, community 1-0 are from those customers who were also placed in community 0 on the first split and in community 1 on the second. Thus, you need to change the upper bounds on the score calculation for column E then requires a check against the previous run in column C:

```
=SUMPRODUCT(TRANSPOSE(Scores!B2:CW2) * B$2:B$101 * (C$2:C$101=C2))
```

The (C$2:C$101=C2) prevents Adams from getting points unless his neighbors are with him on the first split. The Boolean condition basically tests everything in column C2:C101. If any cell in this range equals C2, the value for that row becomes a TRUE; if not, the value becomes a FALSE. Remember, TRUEs and FALSEs are treated as 1s and 0s in Excel. The entirety of the test is stored as a column of TRUEs and FALSEs, which can be multiplied across the other columns and then summed up in the SUMPRODUCT.

We don't have to worry about the Big M constraints. That split was fixed on the last run, so there's nothing nonlinear about this. You can add Boolean calculation into the “Big M” part of the formula to make the final calculation in column E.

```
=SUMPRODUCT(TRANSPOSE(Scores!B2:CW2) * B$2:B$101 * (C$2:C$101=C2)) +
(1-B2) * SUMPRODUCT(TRANSPOSE(ABS(Scores!B2:CW2)) * (C$2:C$101=C2))
```

Similarly, you can add the same elements to the upper-bound column in F.

```
=SUMPRODUCT(TRANSPOSE(Scores!B2:CW2) * (1-(B$2:B$101)) * (C$2:C$101=C2)) +
B2 * SUMPRODUCT(TRANSPOSE(ABS(Scores!B2:CW2)) * (C$2:C$101=C2))
```

All you've done is silo-ed the problem—those who were split into community 0 the first time around have their own little world of scores to play with, and the same goes for those who ended up in 1 the first time.

And here's the cool part—you don't have to change the Solver formulation at all! Same formulation, same options! If you're using OpenSolver, it may not have saved your maximum time limit options from the previous tab. Reset the option to 300 seconds. Solve again.

In my run on Split2, I ended up with a final modularity of 0.546 (see Figure 5.34), which is a substantial improvement over 0.464. That means that splitting was a good idea. (Your solution may end up different and possibly better.)

| Customers | Community | Last Run | Score | UB1 | UB2 | Total Score |
|---|---|---|---|---|---|---|
| Adams | 0 | 1 | 7.832 | 12.303 | 7.832 | 0.546 |
| Allen | 1 | 0 | 3.497 | 3.497 | 6.224 | |
| Anderson | 0 | 0 | 10.561 | 11.045 | 10.561 | |
| Bailey | 0 | 1 | 9.510 | 14.345 | 9.510 | |
| Baker | 1 | 0 | 4.246 | 4.246 | 7.216 | |
| Barnes | 1 | 0 | 4.497 | 4.497 | 6.958 | |
| Bell | 0 | 0 | 10.561 | 11.045 | 10.561 | |
| Bennett | 1 | 1 | 4.182 | 4.182 | 17.497 | |
| Brooks | 1 | 0 | 2.995 | 2.995 | 6.576 | |
| Brown | 0 | 1 | 8.392 | 12.552 | 8.392 | |
| Butler | 1 | 0 | 1.499 | 1.499 | 2.431 | |
| Campbell | 0 | 0 | 8.124 | 9.126 | 8.124 | |
| Carter | 0 | 1 | 8.951 | 12.755 | 8.951 | |
| Clark | 1 | 0 | 4.497 | 4.497 | 6.902 | |

Figure 5.34: The optimal solution for Split2

## And...Split3: Split with a Vengeance

Should you stop here or should you keep going? The way to tell is to split again, and if Solver can't do better than 0.546, you're through.

Start by creating a Split3 tab, renaming Last Run to Last Run 2, and then inserting a new Last Run in column C. Then copy the values from column B into C.

Add more checks to the upper bounds for community assignments in the previous run. For example, F2 becomes the following:

```
=SUMPRODUCT(TRANSPOSE(Scores!B2:CW2) * B$2:B$101 * (C$2:C$101=C2) * (D$2:D$101=D2)) +
(1-B2)*SUMPRODUCT(TRANSPOSE(ABS(Scores!B2:CW2)) * (C$2:C$101=C2) * (D$2:D$101=D2))
```

Once again, the Solver formulation doesn't change. Reset your maximum solving time if need be, click Solve, and let the model run its course. In the case of my model, I saw virtually no improvement in modularity (see Figure 5.35).
