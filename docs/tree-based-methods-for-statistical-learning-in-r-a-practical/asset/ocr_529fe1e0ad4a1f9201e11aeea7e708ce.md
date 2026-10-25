```
#>   [,1] [,2]
#> [1,]    0    1
#> [2,]    8    0
```

Although I restricted each tree to a max depth of two, the tree on the far left side of Figure 2.26 actually coincides with the optimal tree I would've obtained using 10-fold cross-validation and the 1-SE rule (assuming unequal misclassification costs, of course), and shows that having to work overtime, as well as having a lower monthly income, was associated with the highest predicted probability of attrition (p = 0.70)

To further illustrate pruning using the 1-SE rule in rpart, let's look at a tree based on altered priors (tree3) with the full set of features. Below, I refit the same altered priors tree using all available features to maximum depth (i.e., intentionally overgrow the tree); the cross-validation results and pruned tree diagram are displayed in Figure 2.27 (p. 109). The top plot in Figure 2.27 shows the cost-complexity pruning results as a function of the number of splits (top axis). If I were to prune using the 1-SE rule, I would select the tree corresponding to the point farthest to the left that's below the horizontal line (the horizontal line corresponds to 1-SE above the minimum error). In this case, we would end up with a tree containing just four splits, as seen in the bottom plot in Figure 2.27.

```
library(rpart)
```

```
# Saturated tree with altered priors using all predictors
att.cart <-
  rpart(Attrition ~ ., data = attrition, cp = 0, minsplit = 2,
        parms = list("prior" = c(1 - 0.6059444, 0.6059444)))
```

```
# Plot pruning results (Figure 2.27)
par(mfrow = c(2, 1))
plotcp(att.cart, upper = "splits")
(att.cart.1se <- prune_se(att.cart, se = 1))
```

```
#> n= 1470
#>
#> node), split, n, loss, yval, (yprob)
#>   * denotes terminal node
#>
#>  1) root 1470 579.0 Yes (0.394 0.606)
#>   2) OverTime=No 1054 413.0 No (0.518 0.482)
#>     4) TotalWorkingYears>=2.5 966 304.0 No (0.577 0.423)
#>       8) StockOptionLevel>=0.5 568 117.0 No (0.684 0.316) *
#>       9) StockOptionLevel< 0.5 398 163.0 Yes (0.465 0.535)
#>        18) JobRole=Healthcare_Representative,Human_Resources,Mana...
#>        19) JobRole=Laboratory_Technician,Research_Scientist,Sales...
#>     5) TotalWorkingYears< 2.5 88  27.7 Yes (0.203 0.797) *
```