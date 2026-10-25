
```
#> 3) Overtime=Yes 416 136.0 Yes (0.221 0.779) *
tree_diagram(att.cart.lse, tweak = 0.8)
```

### 2.9.5 Example: letter image recognition

The goal of this example is to build an image classifier using a simple decision tree that incorporates additional information about the true class priors for a multiclass outcome with J = 26 classes. The letter image recognition data, which are available in R via the mlbench package [Leisch and Dimitriadou., 2021], contains 20,000 observations on 17 variables. Each observation corresponds to a distorted black-and-white rectangular pixel image of a capital letter from the English alphabet (i.e., A–Z). A total of 16 ordered features was derived from each image (e.g., statistical moments and edge counts) which were then scaled to be integers in the range 0–15. The objective is to identify each letter using the 16 ordered features. Frey and Slate [1991] first analyzed the data using Holland-style adaptive classifiers, and reported an accuracy of just over 80%.

To start, I'll load the data and split it into train/test sets using a 70/30 split:

```
library(treeisc) # for prune_se()

data(LetterRecognition, package = "mlbench")
lr <- LetterRecognition # shorter name for brevity
set.seed(1051) # for reproducibility
trn.ids <- sample(nrow(lr), size = 14000, replace = FALSE)
lr.trn <- lr[trn.ids, ] # training data
lr.tst <- lr[-trn.ids, ] # test data
```

Next, I'll use rpart() to fit a classification tree that's been pruned using the 1-SE rule with 10-fold cross-validation, and see how accurate it is on the test sample:

```
set.seed(1703) # for reproducibility
lr.cart <- rpart(letter ~ ., data = lr.trn, cp = 0, xval = 10)
lr.cart <- prune_se(lr.cart, se = 1) # prune using 1-SE rule

# Compute accuracy on test set
pred <- predict(lr.cart, newdata = lr.tst, type = "class")
sum(diag(table(pred, lr.tst$letter))) / length(pred)
```

```
#> [1] 0.813
```

The data are also available from the UCI Machine Learning Repository: https://archive.ics.uci.edu/ml/datasets/Letter+Recognition.

Nice, an overall accuracy of 81%—similar to the best accuracy reported in Frey and Slate [1991]. But don't be fooled, the data have been artificially balanced:

```r
table(lr$letter)
```

| Letter | Frequency | Letter | Frequency |
|--------|-----------|--------|-----------|
| A | 789 | N | 783 |
| B | 766 | O | 753 |
| C | 736 | P | 803 |
| D | 805 | Q | 783 |
| E | 768 | R | 758 |
| F | 775 | S | 748 |
| G | 773 | T | 796 |
| H | 734 | U | 813 |
| I | 755 | V | 764 |
| J | 747 | W | 752 |
| K | 739 | X | 787 |
| L | 761 | Y | 786 |
| M | 792 | Z | 734 |

As noted in Matloff [2017, Sec. 5.8], this is unrealistic since some letters tend to appear much more frequently than others in English text. For example, assuming balanced classes, `rpart()` uses a prior probability for the letter “A” of $\pi_A = 1/26 \approx 0.0384$, when in fact $\pi_A$ is closer to 0.0855.

A proper analysis should take these frequencies into account, which is easy enough to do with classification trees. Fortunately, the correct letter frequencies are conveniently available in the **regtools** package [Matloff, 2019]. Below, I’ll refit the model including the updated (and more realistic) class priors. I’ll then sample the test data so that the resulting class frequencies more accurately reflect the true prior probabilities of each letter:

```
data(ltrfreqs, package = "regtools")
```

```
# Compute correct class priors
priors <- ltrfreqs$percent
priors <- priors / sum(priors) # class priors should sum to 1
names(priors) <- ltrfreqs$ltr
priors <- priors[order(ltrfreqs$ltr)]
```

```
# Refit tree using correct priors
set.seed(1718) # for reproducibility
lr.cart.priors <- rpart(letter ~ ., data = lr.trn, cp = 0,
parms = list(prior = priors))
lr.cart.priors <- prune_se(lr.cart.priors, se = 1)
```

```
# Sample test set to reflect correct class frequencies
ltrfreqs2 <- ltrfreqs
names(ltrfreqs2) <- c("letter", "prior")
ltrfreqs2$prior <- ltrfreqs2$prior / sum(ltrfreqs2$prior)
temp <- merge(lr.tst, ltrfreqs2) # merge the two data sets
set.seed(1107) # for reproducibility
lr.tst2 <- temp[sample(nrow(temp), replace = TRUE,
prob = temp$prior), ]
```

Finally, let’s compare the two CART fits on the modified test set that reflects the more correct class frequencies:

Based on the English letter frequencies reported at http://practicalcryptography.com.

```
pred2 <- predict(lr.cart, newdata = lr.tst2, type = "class")
pred3 <- predict(lr.cart.priors, newdata = lr.tst2, type = "class")
sum(diag(table(pred2, lr.tst2$letter))) / length(pred2)
#> [1] 0.803
sum(diag(table(pred3, lr.tst2$letter))) / length(pred3)
#> [1] 0.858
```

While the error of the original model based on equal priors decreased (albeit, not by much), the tree incorporating true prior information did much better. Woot!

## 2.10 Discussion

CART is one of the best off-the-shelf machine learning algorithms in existence, but it’s not without its drawbacks. In closing, let’s summarize many of the advantages and disadvantages of the CART algorithm for decision tree induction. While the emphasis here is on CART, much of this discussion equally applies to other decision tree algorithms as well (e.g., C4.5/C5.0).

### 2.10.1 Advantages of CART

- **Small trees are easy to interpret.** Decision trees are often hailed as being simple and interpretable, relative to more complex algorithms. However, this is really only true for small trees with relatively few splits, like the one from Figure 2.22 (p. 95).

- **Trees scale well to large _N_.** Individual decision trees scale incredibly well to large data sets, especially if most of the features are ordered, or categorical with relatively few categories. Even in the extreme cases, various shortcuts and approximations can be used to reduce computational burden (see, for example, Section 2.4).

- **The leaves form a natural clustering of the data.** All observations that coinhabit a terminal node necessarily satisfied all the same conditions when traversing the tree; in this sense, the records within a terminal node should be similar with respect to the feature values and can be considered _nearest neighbors_. We’ll revisit this idea in Section 7.6.

- **Trees can handle data of all types.** Trees can naturally handle data of mixed types, and categorical features do not necessarily have to be numerically re-encoded, like in linear regression or neural networks. Trees are also invariant to monotone transformations of the predictors; that is, they only care about the rank order of the values of each ordered feature. For example, there's no need to apply logarithmic or square root transformations to any of the features like you might in a linear model.

- **Automatic variable selection.** CART selects variables and splits one step at a time (“...like a carpenter that makes stairs”); hence the quote at the beginning of the chapter. If a variable cannot meaningfully partition the data into homogeneous subgroups, it will not likely be selected as a primary splitter. If it does, it’ll likely get snipped off during the pruning phase.

- **Trees can naturally handle missing data.** As discussed in Section 2.7, CART can naturally avoid many of the problems caused by missing data by using surrogate splits (i.e., back up splitters that can be used whenever missing values are encountered during prediction).

- **Trees are completely nonparametric.** CART is fully nonparametric. It does not require any distributional assumptions, and the user does not have to specify any parametric form for the model, like in linear regression. It can also automatically handle nonlinear relationships (although it tends be quite biased since it uses step function to approximate potentially smooth surfaces) and interactions.

### 2.10.2 Disadvantages of CART

- **Large trees are difficult to interpret.** Large tree diagrams, like the ones in Figure 2.23 (p. 97), can be difficult to interpret and are probably not very useful to the end user. Fortunately, various interpretibility techniques, like variable importance plots and PDPs, can help alleviate this problem. Such techniques are the topic of Chapter 6.

- **CART's splitting algorithm is quite greedy.** CART makes splits that are locally optimal. That is, the algorithm does not look through all possible tree structures to globally optimize some performance metric; that would be unfeasible, even for a small number of features. Instead, the algorithm recursively partitions the data by looking for the next best split at each stage. This is analogous to the difference between _forward-stepwise selection_ and _best-subset selection_. Greedy algorithms use a more constrained search and tend to have lower variance but often pay the price in bias. Chapters 5–8 discuss several strategies for breaking the bias-variance-tradeoff by combining many decision trees together.

- **Splits lower on the tree are less accurate.** Data is essentially taken away after each split, making splits further down the tree less accurate (and noisy) compared to splits near the root node. This is part of the reason why binary
