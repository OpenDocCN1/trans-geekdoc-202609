
```r
ctrl <- # control tree-specific parameters
rpart::rpart.control(cp = 0, maxdepth = depth, minbucket = 10)
for (tree in seq_len(ntree)) {
  id <- sample.int(nrow(X), size = floor(subsample * nrow(X)))
  samp <- X[id, ]
  samp$pr <- sign(y[id] - yhat[id]) # use signed residual
  trees[[tree]] <-
    rpart::rpart(pr ~ ., data = samp, control = ctrl)
# -----------------------------------------------------------
# Line search; update terminal node estimates using median
# -----------------------------------------------------------
where <- trees[[tree]]$where # terminal node assignments
map <- tapply(samp$pr, INDEX = where, FUN = median)
trees[[tree]]$frame$yval[where] <- map[as.character(where)]
#
# Could use partykit instead:
#
# trees[[tree]] <- partykit::as.party(trees[[tree]])
# med <- function(y, w) median(y) # see ?partykit::predict.party
# yhat <- yhat +
#   shrinkage * partykit::predict.party(trees[[tree]],
#                                       newdata = X, FUN = med)
# -----------------------------------------------------------------
yhat <- yhat + shrinkage * predict(trees[[tree]], newdata = X)
}
res <- list("trees" = trees, "shrinkage" = shrinkage,
            "depth" = depth, "subsample" = subsample, "init" = init)
class(res) <- "ladboost"
res
}
```

## 8.5.1 Example: predicting home prices

Let’s apply the `l1boost()` function to the Ames housing data. Below, I use the same train/test split for the Ames housing data we’ve been using throughout this book, then call `l1boost()` to fit a GBM to the training set; here, I’ll use a shrinkage factor of \(\nu = 0.1\):

```r
library(treeemisc)

# Split Ames data into train/test sets using a 70/30 split
ames <- as.data.frame(AmesHousing::make_ames())
ames$Sale_Price <- ames$Sale_Price / 1000 # rescale response
set.seed(4919) # for reproducibility
id <- sample.int(nrow(ames), size = floor(0.7 * nrow(ames)))
ames.trn <- ames[id, ]
ames.tst <- ames[-id, ]
```

```r
# Fit a gradient tree boosted ensemble with 500 trees
set.seed(1110) # for reproducibility
ames.bst <-
  l1boost(subset(ames.trn, select = -Sale_Price), # features only
          y = ames.trn$Sale_Price, ntree = 500, depth = 4,
          shrinkage = 0.1)
```

The test RMSE as a function of the number of trees in the ensemble is computed below using the previously defined predict() method; the results are shown in Figure 8.4 (black curve). For brevity, the code uses sapply() to essentially iterate cumulatively through the B = 500 trees and computes the test RMSE for the first tree, first two trees, etc. For comparison, the test RMSEs from a default RF are also computed and displayed in Figure 8.4 (yellow curve). In this example, the GBM slightly outperforms the RF.

```r
set.seed(1128) # for reproducibility
ames.rfo <- # fit a default RF for comparison
  randomForest(subset(ames.trn, select = -Sale_Price),
               y = ames.trn$Sale_Price, ntree = 500,
               # Monitor test set performance (MSE, in this case)
               xtest = subset(ames.tst, select = -Sale_Price),
               ytest = ames.tst$Sale_Price)
```

```r
# Helper function for computing RMSE
rmse <- function(pred, obs, na.rm = FALSE) {
  sqrt(mean((pred - obs)^2, na.rm = na.rm))
}
```

```r
# Compute RMSEs from both models on the test set as a function of the
# number of trees in each ensemble (i.e., B = 1, 2, ..., 500)
rmses <- matrix(nrow = 500, ncol = 2) # to store results
colnames(rmses) <- c("GBM", "RF")
rmses[, "GBM"] <- sapply(seq_along(ames.bst$trees), FUN = function(B) {
  pred <- predict(ames.bst, newdata = ames.tst, ntree = B)
  rmse(pred, obs = ames.tst$Sale_Price)
}) # add GBM results
rmses[, "RF"] <- sqrt(ames.rfo$test$mse) # add RF results
```

## 8.6 Interpretability

Interpreting GBMs is no different from any other nonparametric model. For example, Section 5.4 discussed how the individual tree-based importance scores (Section 2.8) can be aggregated across all the trees in an ensemble to form a more stable measure of predictor importance; however, as with CART and RFs, this measure is also biased for GBMs, although, the permutation importance method (Section 6.1.1) applies equally well to GBMs, or any supervised learning model, for that matter. PDPs and ICE plots can be used to visualize the global and local effect that subsets of features have on the model’s predictions, respectively. Shapley values, among other techniques, can be used to infer the contribution each feature value has on the difference between its associated prediction and the model’s baseline (or average training) prediction, which can also be used to generate global measures of both feature importance and feature effects. The next two sections discuss specialized interpretability techniques often associated with GBMs.

![](img/2c227bfb3620dc3d159fa5e6598afa30_344_0.png)

FIGURE 8.4: Root mean-squared error for the Ames housing test set as a function of $B$, the number of trees in the ensemble. Here, I show both a GBM (black curve) and a default RF (yellow curve). In this case, gradient tree boosting with LS loss, a shrinkage of $\lambda = 0.1$, and a maximum tree depth of $d = 4$ (black curve) slightly outperforms a default RF (yellow curve).

### 8.6.1 Faster partial dependence with the recursion method

For regression trees based on single-variable splits, Friedman [2001] described a fast procedure for computing the partial dependence of $\hat{f}(x)$ on a subset of features using a weight traversal of each tree (henceforth referred to as the recursion method). In particular$^k$, if a split node involves an input feature from the interest set ($z_c$), the corresponding left or right branch is followed; otherwise both branches are followed, each branch being weighted by the fraction of training observations that entered that branch. Finally, the partial dependence is given by a weighted average of all the visited terminal node values.

The idea is not specific to gradient tree boosting (e.g., it could also be applied to a RF), but as far as I'm aware, it's only implemented in a couple of open source packages: R's **gbm** package (which **pdp** takes full advantage of) and the **sklearn.inspection** module, which supports the recursion method only for certain tree-based estimators. Most other implementations rely on the brute force method described in Section 6.2.1.

### 8.6.1.1 Example: predicting email spam

Let's illustrate with the email spam example (Section 1.4.5). Here, I used the R package **gbm** to fit a GBM using log loss, $B = 4,043$ depth-2 regression trees (found using 5-fold cross-validation), a shrinkage factor of $\nu = 0.01$.

To gain an appreciation for the computational speed-up of the recursion method (which is implemented in **gbm**), I computed Friedman's $H$-statistic for all 1,596 pairwise interactions, which took roughly five minutes! The largest pairwise interaction occurred between **address** and **receive**. The partial dependence of the log-odds of spam on the joint frequencies of **address** and **receive** is displayed in Figure 8.5. Using the fast recursion method, this took roughly a quarter of a second to compute, compared to the brute force method, which took almost 500 seconds.

### 8.6.2 Monotonic constraints

Increasing the interpretability of a model without sacrificing too much in the way of accuracy is useful in many real-world applications. For example, prior knowledge may be available (e.g., from subject matter experts or historical data) indicating that a given feature should in general have a positive (or negative) effect on the expected outcome. With GBMs, we can often increase interpretability by enforcing such _monotonic constraints_.

In gradient tree boosting, monotonic constraints enforce a specific splitting strategy in each of the constituent regression trees, where binary splits of a variable in one direction either always increase (monotone increasing) or decrease (monotone decreasing) the mean response in the resulting child node. For example, in a model with just two features, $x_1$ and $x_2$, if we specified a

$^k$Deets taken from the partial dependence documentation on scikit-learn's website: https://scikit-learn.org/stable/modules/partial_dependence.html.
