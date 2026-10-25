
mushroom.tree$variable.importance
```
#>             odor       spore.print.color
#>        3823.407        2834.187
#>        gill.color   stalk.surface.above.ring
#>        2322.460        2035.816
#> stalk.surface.below.ring          ring.type
#>        2030.555        2026.526
#>     stalk.color.below.ring       stalk.root
#>        53.933           25.600
#>     stalk.color.above.ring       veil.color
#>        17.546           16.315
#>              cap.surface           cap.color
#>        15.360           14.032
#>              habitat           cap.shape
#>        13.409            3.840
#>        gill.attachment
#>         0.585
```

In many cases, predictors that weren't used in the tree will have a non-zero importance score. The reason is that surrogate splits are also incorporated into the calculation. In particular, a variable may effectively appear in the tree more than once, either as a primary or surrogate splitter. The variable importance measure for a particular feature is the sum of the gains associated with each split for which it was the primary variable, plus the gains (adjusted for agreement) associated with each split for which it was a surrogate. You can turn off surrogates by setting `maxsurrogate = 0` in `rpart.control()`.

How does _k_-fold cross-validation (Section 2.5.2) in **rpart** work? The `rpart()` function does internal 10-fold cross-validation by default. According to **rpart**'s documentation, 10-fold cross-validation is a reasonable default, and has been shown to be very reliable for screening out “pure noise” features. The number of folds (_k_) can be changed, however, using the `xval` argument in `rpart.control()`.

You can visualize the cross-validation results of an "rpart" object using `plotcp()`, as illustrated in Figure 2.21 for the `mushroom.tree` object. A good rule of thumb in choosing `cp` for pruning is to use the leftmost value for which the average cross-validation score lies below the horizontal line; this coincides with the 1-SE rule discussed in Section 2.5.2.1. The columns labeled "`xerror`" and "`xstd`" provide the cross-validated risk and its corresponding standard error, respectively (Section 2.5).

```
plotcp(mushroom.tree, upper = "splits", las = 1) # Figure 2.21
mushroom.tree$cptable # print cross-validation results
```

```
#>        CP nsplit rel error   xerror      xstd
#> 1 0.96936      0 1.00000 1.000000 0.011501
#> 2 0.01839      1 0.03064 0.030644 0.002777
#> 3 0.00613   2   0.01226 0.012257 0.001764
#> 4 0.00204   3   0.00613 0.006129 0.001249
#> 5 0.00102   5   0.00204 0.002043 0.000722
#> 6 0.00000   7   0.00000 0.000511 0.000361
```

![](img/2c227bfb3620dc3d159fa5e6598afa30_110_0.png)

FIGURE 2.21: Cross-validation results from the fitted mushroom.tree object. A good choice of cp for pruning is often the leftmost value for which the mean lies below the horizontal line; this corresponds to the optimum value based on the 1-SE rule.

Don't be confused by the fact that the cp values between printcp() (and hence the $cptable component of an "rpart" object) and plotcp() don't match. The latter just plots the geometric means of the CP column listed in printcp() (these relate to the \(\beta_i\) values used in the k-fold cross-validation procedure described in Section 2.5). Any cp value between two consecutive rows will produce the same tree. For instance, any cp value between 0.002 and 0.001 will produce a tree with five splits. Also, these correspond to a scaled version of the complexity values \(\alpha_i\) from Section 2.5. Note that rpart scales the CP column, as well as the error columns, by a factor inversely proportional to the risk of the root node, so that the associated training error ("rel error") for the root node is always one (i.e., the first row in the table); which in this case is 1 / (3916/8124) ≈ 2.075. Dividing through by this scaling factor should return the raw \(\alpha_i\) values; the first three correspond to the values I computed by hand back in Section 2.5:

```
mushroom.tree$cptable[1L:3L, "CP"] / (8124 / 3916)
#>   1   2   3
#> 0.46726 0.00886 0.00295
```

Consequently, setting cp = 1 will always result in a tree with no splits. The default, cp = 0.01, has been shown to be useful at “pre-pruning” the trees in a way such that the cross-validation step results in only the removal of 1–2 layers, although it can also occasionally over-prune. In practice, it seems best to set cp = 0, or some other number smaller than the default, and use the cross-validation results to choose an optimal subtree.

Using the 1-SE rule would suggest a tree with 5, or possibly 7, splits. However, since our main objective is to construct a simple rule-of-thumb for classifying the edibility of mushrooms, it seems like the simpler model with only a single split (i.e., a decision stump) will suffice; it only misclassifies 3% of the poisonous mushrooms as edible. To prune an rpart tree, use the prune() function with a specified value of the complexity parameter:

```
tree_diagram(prune(mushroom.tree, cp = 0.1)) # Figure 2.22
```

![](img/2c227bfb3620dc3d159fa5e6598afa30_111_0.png)

FIGURE 2.22: Decision tree diagram for classifying the edibility of mushrooms; in this case, the result is a decision stump.

The tree diagram displayed in Figure 2.22 provides us with a handy rule of thumb for classifying mushrooms as either edible or poisonous. If the mushroom smells fishy, foul, musty, pungent, spicy, or like creosote, it’s likely poisonous. In other words, if it smells bad, don’t eat it!

## 2.9.3 Example: predicting home prices

In this section, I'll use rpart to build a regression to the Ames housing data (Section 1.4.7). I'll also show how to easily prune an rpart tree using the 1-SE rule via treemisc's prune_se() function. The code chunk below loads in the data before splitting it into train/test sets using a 70/30 split:

```
ames <- as.data.frame(AmesHousing::make_ames())
ames$Sale_Price <- ames$Sale_Price / 1000 # rescale response
set.seed(2101) # for reproducibility
trn.id <- sample.int(nrow(ames), size = floor(0.7 * nrow(ames)))
ames.trn <- ames[trn.id, ] # training data/learning sample
ames.tst <- ames[-trn.id, ] # test data
```

Next, I'll intentionally fit an overgrown regression tree by setting cp = 0; in a regression tree, rpart will not attempt a split unless it increases the overall R^2 by cp, so setting cp = 0 will cause the tree to continue splitting until some other stopping criterion is met, such as minimum node size (in rpart, the default minimum number of observations that must exist in a node in order for a split to be attempted is 20). I'll also compare the RMSE between the train and test sets:

```
library(rpart)
library(treemisc) # for prune_se() function

# Fit a regression tree with no penalty on complexity
set.seed(1547) # for reproducibility
ame.tree <- rpart(Sale_Price ~ ., data = ames.trn, cp = 0)

rmse <- function(pred, obs) { # computes RMSE
  sqrt(mean((pred - obs) ^ 2))
}

# Compute train RMSE
rmse(predict(ame.tree, newdata = ames.trn), obs = ames.trn$Sale_Price)
#> [1] 23.4

# Compute test RMSE
rmse(predict(ame.tree, newdata = ames.tst), obs = ames.tst$Sale_Price)
#> [1] 31.4
```

The tree is likely overfitting, as indicated by the relatively large discrepancy between the train and test RMSE. Let's see if pruning the tree can help. The prune_se() function from treemisc can be used to prune rpart trees using the 1-SE rule, as illustrated below:

```
ame.tree.1se <- prune_se(ame.tree, se = 1) # prune using 1-SE rule

# Train RMSE on pruned tree
rmse(predict(ame.tree.1se, newdata = ames.trn),
 obs = ames.trn$Sale_Price)
#> [1] 29.5

# Test RMSE on pruned tree
rmse(predict(ame.tree.1se, newdata = ames.tst),
 obs = ames.tst$Sale_Price)
#> [1] 34.1
```

A smaller discrepancy, but the pruned tree is slightly less accurate than the unpruned tree on the test set. So did pruning really help here? It depends on how you look at it. Both trees are displayed in Figure 2.23 without text or labels. The unpruned tree has 169 splits while pruning with the 1-SE rule and cross-validation resulted in a subtree with only 33 splits—a much more parsimonious tree

![](img/2c227bfb3620dc3d159fa5e6598afa30_113_0.png)

FIGURE 2.23: Regression trees for the Ames housing example. Left: unpruned regression tree. Right: pruned regression tree using 10-fold cross-validation and the 1-SE rule.

Even with pruning, we still ended up with a subtree that is too complex to easily interpret. In situations like this, it can be helpful to use different post hoc interpretability techniques to help the end user interpret the model in a way more understandable for humans. For instance, it can be quite informative to look at a plot of variable importance scores, like the Cleveland dot plot displayed in Figure ??; here, the importance scores are scaled to sum to 1 (see the code chunk below). From the results, we can see that the overall quality
