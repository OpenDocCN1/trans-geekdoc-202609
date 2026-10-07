# Multi-Factor Between-Participants Designs 237

variable, instructions. These means are in the right-most column in the upper panels of Table 9.11. A better way to see the possible interaction is to redisplay the means:

| Age Group | Younger | Older |
|---|---|---|
| Format | | 89.00 | 83.25 |
| Web Text | 72.25 | 72.50 |

The pattern of means indicates that the advantage of the young adults over the older adults is, as hypothesized, greater when information is presented in the web format. The significance test of this interaction is a test of the null hypothesis, *averaging over the two levels of instructions*, no difference in the magnitude of the effect as a function of age group.

Calculating the interaction sum of squares is generally too tedious to do by hand. However, in the case of interactions based on 1 df, we can represent the interaction as a difference between differences. This makes hands much manageable; much importantly, expressing a $2 x 2$ interaction as a difference between simple effects is a better way to understand what is being tested. Let $I$ indicate the interaction effect; then,

$I_{FA} = (89.00 - 72.25) - (83.25 - 72.50) = 6.00$

In words, the effect of format is 6 greater for young adults than for older adults. Rearranging them, this $FA$ interaction can be rewritten as a difference between the sums of diagonal cells:

$I_{FA} = (89.00 + 72.50) - (83.25 + 72.25)$

If we calculate the averages of the two diagonal sums, we have the basis for a test of the difference between two means; these are $(89.00 + 72.50)/2$, 80.75, and $(83.25 + 72.25)/2$, or 77.75. With our example in testing the main effect of format, we can test the $FA$ interaction by comparing these two means via a $t$ test:

```
$t = \frac{80.75 - 77.75}{\sqrt{154(\frac{1}{40} + \frac{1}{40})}} = 1.081$
```

Alternatively, applying Equation 9.10, we can construct an $F$ test:

```
$F = \frac{(80.75 - 77.75)^2}{\frac{1}{40} + \frac{1}{40}} = 1.169 = 1.081^2$
```

The degrees of freedom for the error term are $abc(n - 1)$, or 72 in this design, assuming 10 participants in each cell of the cells. The $F$ of 1.17 is not significant on 1 and 72 $df$ and therefore we lack sufficient evidence to reject the hypothesis of no interaction. In other