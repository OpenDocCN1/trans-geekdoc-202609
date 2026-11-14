the total modularity scores, so Adams’ score will want to rise until it bumps up against the lowest of these two constraining formulas.

But how do you know which score calculation corresponding to Adams’ actual community assignment is the lowest?
You don't.

To fix that, you need to _deactivate_ whichever of those two formulas isn't in play. If Adams is assigned a 1, the first formula becomes an upper bound, and the second formula is _turned off_. If Adams is a zero, you have the opposite.

How do you turn off one of the two upper bounds? Add a “Big M to it”—just big enough that its bound is meaningless, because the legit bound is lower.

Consider this modification to the first formula:

```
=SUMPRODUCT(TRANSPOSE(Scores!B2:CW2) * B$2:B$101) + SUM(ABS(Scores!B2:CW2)) * (1-B2)
```

If Adams is assigned to community 1, the addition you made at the end of the formula turns to 0 (because you’re multiplying by 1-B2). In this way, the formula becomes identical to the first one you examined. But if Adams gets assigned to community 0, this formula no longer applies and needs to be turned off. So the SUM(ABS(Scores!B2:CW2)) * (1-B2) piece of the formula adds one times the sum of all the absolute values of the scores Adams could possibly get, which guarantees the formula is higher than its flipped version that’s now in play:

```
=SUMPRODUCT(TRANSPOSE(Scores!B2:CW2) * (1-B$2:B$101)) + SUM(ABS(Scores!B2:CW2)) * B2
```

All you’re doing is setting Adams’ score to be less than or equal to the correct calculation and removing the other formula from consideration by making it larger.

So then in column C create a score column that will be a decision variable. In columns D and E in the spreadsheet you can place these two formulas as upper bounds on the score (see Figure 5.29).

Go ahead and test it by toggling between the values of 1 and 0 in B2!

![](bbox=[0.135, 0.705, 0.85, 0.905])