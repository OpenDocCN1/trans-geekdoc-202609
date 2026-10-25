
```
#> probabilities: 0.980 0.020
#>
#> Node number 3: 98 observations
#> predicted class=Genuine   expected loss=0 P(node) =0.49
#> class counts:   0  98
#> probabilities: 0.000 1.000
```

Using all the predictors results in the same decision stump that was displayed in Figure 2.18. As it turns out, the best tree uses a single split on the length of the diagonal (in mm) and only misclassifies two of the genuine banknotes in the learning sample. In addition to the chosen splitter, `diagonal`, we also see a description of the competing splits (four by default) and surrogate splits (five by default); note that these match the surrogate splits I found manually back in Section 2.7. For example, if I didn’t include `diagonal` as a potential feature, then `bottom` would’ve been selected as the primary splitter because it gave the next best reduction to weighted impurity (`improve=71.59091`).

While the `rpart` package provides `plot()` and `text()` methods for plotting and labeling tree diagrams, respectively, the resulting figures are not as polished as those produced by other packages; for example, `rpart.plot` [Milborrow, 2021b] and `partykit` [Hothorn and Zeileis, 2021]. All the tree diagrams in this chapter were constructed using a simple wrapper function around `rpart.plot()` called `tree_diagram()`, which is part of `treemisc`; see `?rpart.plot::rpart.plot` and `?treemisc::tree_diagram` for details. For example, the tree diagram from Figure 2.2 (p. 43) can be constructed using:

```
treemisc::tree_diagram(bn.tree)
```

Figure 2.19 shows a tree diagram depicting the primary split (left) as well as the second best surrogate split (right). In the printout from `summary()`, we also see the computed agreement and adjusted agreement for each surrogate. From Figure 2.19, we can see that the surrogate sends (66 + 91) / 200 ≈ 0.785 of the observations in the same direction as the primary split (agreement). The majority rule gets 102 correct, giving an adjusted agreement of (66 + 91 – 102) / (200 – 102) ≈ 0.561.

![](img/2c227bfb3620dc3d159fa5e6598afa30_105_0.png)

FIGURE 2.19: Decision stump for the Swiss banknote example (left) and one of the surrogate splits (right).

### 2.9.2 Example: mushroom edibility

In this section, we’ll use `rpart` to fit a classification tree to the mushroom data, and explore a bit more of the output and fitting process. Recall from Section 1.4.4, that the overall objective is to find a simple rule of thumb (if possible) for avoiding potentially poisonous mushrooms. For now, I’ll stick with `rpart`’s defaults (e.g., the splitting rule is the Gini index), but set complexity parameter, cp, to zero (cp = 0) for a more complex tree.

The default setting in rpart is cp = 0.01.

Although the tree construction itself is not random, the internal cross-validation results are, so I'll also set the random number seed before calling rpart():

```
mushroom <- treemisc::mushroom

# Fit a default tree with zero penalty on tree size
set.seed(1054) # for reproducibility
(mushroom.tree <- rpart(Edibility ~ ., data = mushroom, cp = 0))

#> n= 8124
#>
#> node), split, n, loss, yval, (yprob)
#>   * denotes terminal node
#>
#>  1) root 8124 3920 Edible (0.51797 0.48203)
#>  2) odor=almond,anise,none 4328 120 Edible (0.97227 0.02773)
#>  4) spore.print.color=black,brown,buff,chocolate,orange,purple...
#>    8) stalk.color.below.ring=brown,gray,orange,pink,red,white ...
#>  16) stalk.color.below.ring=gray,orange,pink,red,white 4152 ...
#>    32) habitat=grasses,meadows,paths,urban,waste,woods 3952...
#>    33) habitat=leaves 200   8 Edible (0.96000 0.04000)
#>    66) cap.surface=smooth 192   0 Edible (1.00000 0.00000...
#>  67) cap.surface=grooves,scaly 8   0 Poison (0.00000 1...
#> 17) stalk.color.below.ring=brown 80 16 Edible (0.80000 0...
#> 34) stalk.root=bulbous 64 0 Edible (1.00000 0.00000) *
#> 35) stalk.root=missing 16 0 Poison (0.00000 1.00000) *
#> 9) stalk.color.below.ring=yellow 24 0 Poison (0.00000 1...
#> 5) spore.print.color=green 72 0 Poison (0.00000 1.00000) *
#> 3) odor=creosote,fishy,foul,musty,pungent,spicy 3796 0 Poiso...
```

This is a complex tree with many splits, so let's use **treemisc**'s `tree_diagram()` function to plot it (see Figure 2.20).

```
tree_diagram(mushroom.tree) # Figure 2.20
```

![](img/2c227bfb3620dc3d159fa5e6598afa30_106_0.png)

FIGURE 2.20: Decision tree diagram for classifying the edibility of mushrooms.

Setting cp = 0 won't necessarily result in the most complex or saturated tree. This is because rpart() sets a number of additional parameters by default, many of which help control the maximum size of the tree; these are printed below for the current mushroom.tree object. For instance, minsplit, which defaults to 20, controls the number of observations that must exist in a node before a split can be attempted.

```
unlist(mushroom.tree$control)
#> minsplit minbucket cp
#> 20 7 0
#> maxcompete maxsurrogate usesurrogate
#> 4 5 2
#> surrogate.style maxdepth xval
#> 0 30 10
```

You can change any of these parameters via `rpart()`'s `control` argument, or by passing them directly to `rpart()` via the ... (pronounced dot-dot-dot) argument. For example, the two calls to `rpart()` below are equivalent. Each one fits a classification tree but changes the default complexity parameter from 0.01 to 0 (`cp = 0`) and the number of internal cross-validations from ten to five (`xval = 5`); see `?rpart::rpart.control` for further details about all the configurable parameters.

```
ctrl <- rpart.control(cp = 0, xval = 5) # can also be a names list
tree <- rpart(Edibility ~ ., data = mushroom, control = ctrl)
tree <- rpart(Edibility ~ ., data = mushroom, cp = 0, xval = 5)
```

Another useful option in `rpart()` is the `parms` argument, which controls how nodes are split in the tree; it must be a named list whenever supplied. Below we print the `tree$parms` component, which in this case is a list containing the class priors, loss matrix, and impurity function used in constructing the tree.

```
mushroom.tree$parms
#> $prior
#> 1 2
#> 0.518 0.482
#>
#> $loss
#> [,1] [,2]
#> [1,] 0 1
#> [2,] 1 0
#>
#> $split
#> [1] 1
```

The `$prior` component defaults to the class frequencies in the root node, which can easily be verified:

```
proportions(table(mushroom$Edibility)) # observed class proportions
#>
#> Edible Poison
#> 0.518 0.482
```

The loss matrix, given by component `$loss`, defaults to equal losses for false positives and false negatives (the off diagonals); there's no loss associated with a correct classification (i.e., the diagonal entries are always zero).

9 In R, functions can have a special ... argument that allows them to take any number of additional arguments; see Wickham [2019, Sec. 6.6] for details.
10 The parms argument only applies to response variables that are categorical (classification trees), counts (Poisson regression), or censored (survival analysis)

The `$split` component displays either a 1 (`split = "gini"`) or 2 (`split = "information"`) (partial matching is allowed). All of these can be changed from their respective defaults by passing a named list to the `parms` argument in the call to `rpart()`. For example, to use the entropy splitting rule, run the following:

```
parms <- list("split" = "information") # use cross-entropy split rule
rpart(Edibility ~ ., data = mushroom, parms = parms)
```

Specifying a loss matrix in `rpart` isn't well-documented, unfortunately. For binary outcomes, the matrix has the following structure:

\( L = \begin{bmatrix} TP & FP \\ FN & TN \end{bmatrix}, \)

where rows represent the observed classes and columns represent the assigned classes. Here, TP, FP, FN, and TN stand for *true positive*, *false positive*, *false negative*, and *true negative*, respectively; for example, a false negative is the case in which the tree misclassifies a 1 as a 0. The order of the rows/columns correspond to the same order as the categories when sorted alphabetically or numerically.

Since there is no cost for correct classification, we take \( TP = TN = 0 \). Setting \( FP = FN = c \), for some constant \( c \) (i.e., treat FPs and FNs equally), will always result in the same splits (although, the internal statistics used in selecting the splits will be scaled differently). When misclassification costs are not equal, specify the appropriate values in the loss matrix. For example, the following tree would treat false negatives (i.e., misclassifying poisonous mushrooms as edible) as five times more costly than false positives (i.e., misclassifying edible mushrooms as poisonous). We could also obtain the same tree by computing the altered priors based on this loss matrix and supplying them via the `parms` argument, but this is left as an exercise to the reader.

```
levels(mushroom$Edibility) # inspect order of levels
(loss <- matrix(c(0, 5, 1, 0), nrow = 2)) # loss matrix
rpart(Edibility ~ ., data = mushroom, parms = list("loss" = loss))
```

The variable importance scores (Section 2.8) are contained in the `$variable.importance` component of the `mushroom.tree` object; they're also printed at the top of the output from `summary()`, but rescaled to sum to 100.
