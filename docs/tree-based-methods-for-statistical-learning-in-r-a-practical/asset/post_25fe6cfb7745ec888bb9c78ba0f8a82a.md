
it comes to probability estimation, and you should make an effort to tune $n_{min}$ as well.

![](img/2c227bfb3620dc3d159fa5e6598afa30_252_0.png)

FIGURE 7.4: Class probability estimation using regression forests (yellow) and classification forests (black) in the Mease simulation. Starting from the top-left and moving clockwise, we have: $n_{min} = 1$ (the typical default for classification forests), $n_{min} = 10$ (the current default for probability forests in R's **ranger** package [Wright et al., 2021]), $n_{min} = 40$ (1% of the learning sample), and $n_{min} = 400$ (10% of the learning sample), respectively. The dashed 45-degree line corresponds to perfect agreement.

### 7.2.2 Subsampling (without replacement)

While a traditional RF (Algorithm 7.1) uses bootstrap sampling (i.e., sample with replacement), it can be useful to subsample the training data without replacement, prior to constructing each tree. This was noted in Section 5.1.3 for bagged tree ensembles, and that discussion equally applies to RFs as well. Furthermore, as I'll discuss in Section 7.5, subsampling with replacement can help eliminate certain bias in computing predictor importance, resulting in variable importance scores that can be used reliably for variable selection even in situations where the potential predictors vary in their scale of measurement or their number of categories. Most RF software includes the option to use subsampling with or without replacement.

![](img/2c227bfb3620dc3d159fa5e6598afa30_253_0.png)

FIGURE 7.5: Mean squared errors (MSEs) from the Mease simulation. Here the MSE between the predicted probabilities and the true probabilities for each simulation are displayed using boxplots. Clearly, in this example, the regression forest (RF) with $n_{min} > 1$ produces more accurate class probability estimates.

### 7.2.3 Random forest from scratch: predicting home prices

To help solidify the basic concepts of an RF, let’s construct one from scratch.$^b$ To do that, we need a decision tree implementation that will allow us to randomly select a subset of features for consideration at each node in the tree. Such arguments are available in the sklearn.tree module in Python, as well as R’s party and partykit packages—unfortunately, this option is not currently available in rpart. In this example, I’ll go with party, since it’s ctree() function is faster, albeit less flexible, than partykit’s implementation.

Below is the definition for a function called crforest(), which constructs a conditional random forest (CRF) [Hothorn et al., 2006a, Strobl et al., 2008a, 2007b], that is, an RF using conditional inference trees (Chapter 3) for the base learners.$^c$ The oob argument will come into play in Section 7.3, so just ignore that part of the code for now. Note that the function returns a list of fitted CTrees that we can aggregate later for the purposes of prediction.

```r
crforest <- function(X, y, mtry = NULL, B = 5, oob = TRUE) {
  min.node.size <- if (is.factor(y)) 1 else 5
  N <- nrow(X) # number of observations
  p <- ncol(X) # number of features
  train <- cbind(X, "y" = y)
  fo <- as.formula(paste("y ~ ", paste(names(X), collapse = "+")))
  if (is.null(mtry)) { # use default definition
    mtry <- if (is.factor(y)) sqrt(p) else p / 3
    mtry <- floor(mtry) # round down to nearest integer
  }
  # CTree parameters; basically force the tree to have maximum depth
  ctrl <- party::ctree_control(mtry = mtry, minbucket = min.node.size,
                               minsplit = 10, mincriterion = 0)
  forest <- vector("list", length = B) # to store each tree
  for (b in 1:B) { # fit trees to bootstrap samples
    boot.samp <- sample(1:N, size = N, replace = TRUE)
    forest[[b]] <- party::ctree(fo, data = train[boot.samp, ],
                                control = ctrl)
    if (isTRUE(oob)) { # store row indices for OOB data
      attr(forest[[b]], which = "oob") <-
        setdiff(1:N, unique(boot.samp))
    }
  }
  forest # return the "forest" (i.e., list) of trees
}
```

Let's test out the function on the Ames housing data, using the same 70/30 split from previous examples (Section 1.4.7). Here, I'll fit a default CRF (i.e., \(mtry = \lfloor p/3 \rfloor\) and \(n_{min} = 5\)) using our new `crforest()` function. (Be warned, this code may take a few minutes to run; the code on the book website includes an optional progress bar and the ability to run in parallel using the **foreach** package [Revolution Analytics and Weston, 2020].)

```r
X <- subset(ames.trn, select = -Sale_Price) # feature columns
set.seed(1408) # for reproducibility
ames.crf <- crforest(X, y = ames.trn$Sale_Price, B = 300)
```

To obtain predictions from the fitted model, we can just loop through each tree, extract the predictions, and then average them together at the end. This can be done with a simple `for` loop, which is demonstrated in the code chunk below. Here, I obtain the averaged predictions from `ames.crf` on the test data and compute the test RMSE.

```r
B <- length(ames.crf) # number of trees in forest
preds.tst <- matrix(nrow = nrow(ames.tst), ncol = B)
for (b in 1:B) { # store predictions from each tree in a matrix
  preds.tst[, b] <- predict(ames.crf[[b]], newdata = ames.tst)
}
pred.tst <- rowMeans(preds.tst) # average predictions across trees

# Root-mean-square error function
rmse <- function(pred, obs, na.rm = FALSE) {
  sqrt(mean((pred - obs) ^ 2, na.rm = na.rm))
}

# Root mean square error on test data
rmse(pred.tst, obs = ames.tst$Sale_Price)

#> [1] 24.3
```

Rather than reporting the test RMSE for the entire forest, we can compute it for each sub-forest of size b <= B to see how it changes as the forest grows. We can do this using a simple for loop, as demonstrated in the code chunk below. (Note that I use drop = FALSE here so that the subset matrix of predictions doesn't lose its dimension when b = 1.)

```r
rmse.tst <- numeric(B) # to store RMSEs
for (b in 1:B) {
  pred <- rowMeans(preds.tst[, 1:b, drop = FALSE], na.rm = TRUE)
  rmse.tst[b] <- rmse(pred, obs = ames.tst$Sale_Price, na.rm = TRUE)
}
```

The above test RMSEs are displayed in Figure 7.6 (black curve). For comparison, I also included the test error for a single CTree fit (horizontal dashed line). Here, the CRF clearly outperforms the single tree, and the test error stabilizes after about 50 trees. Next, I'll discuss an internal cross-validation strategy based on the OOB data.

## 7.3 Out-of-bag (OOB) data

One of the most useful by-products of an RF (or bagging in general, for that matter) is the so-called OOB data (see Step 2) (b) in Algorithm 7.1)$^d$. Recall that an RF, or any bagged tree ensemble, is constructed by combining predictions from decision trees trained on different bootstrap samples.$^e$ Since bootstrapping involves sampling with replacement, each tree in the forest only uses a subset of the original learning sample; hence, for each tree in the forest,

d While the concept of OOB is usually discussed in the context of an RF, it equally applies to bagging and boosting when sampling is involved, regardless if the sampling is done with or without replacement.
e This discussion also applies to subsampling without replacement.

a portion of the original learning sample isn't used—these observations are referred to as out-of-bag (or OOB for short). The OOB data associated with a particular tree can be used to obtain an unbiased estimate of prediction error. The OOB errors can then be aggregated across all the trees in the forest to obtain an overall out-of-sample, albeit unstructured, estimate of the overall prediction performance of the forest.

Since bagging/bootstrapping involves sampling with replacement, the probability that a particular case is not selected in a particular bootstrap sample is

\(\text{Pr}(\text{case } i \notin \text{bootstrap sample } b) = \left(1 - \frac{1}{N}\right)^N .\)

As \(N \to \infty\) it can be shown that \(\left(1 - \frac{1}{N}\right)^N \to e^{-1} \approx 0.368\). In other words, on average, each bootstrap sample contains approximately \(1 - e^{-1} \approx 0.632\) of the original training records; the remaining \(e^{-1} \approx 0.368\) observations are OOB and can be used as an independent validation set for the corresponding tree. This is rather straightforward to observe without a mathematical derivation. The code below computes the proportion of non-OOB observations in \(B = 10000\) bootstrap samples of size \(N = 100\), and averages the results together:

```r
set.seed(1226) # for reproducibility
N <- 100 # sample size
obs <- 1:N # original observations
res <- replicate(10000, sample(obs, size = N, replace = TRUE))
inbag <- apply(res, MARGIN = 2, FUN = function(boot.sample) {
  mean(obs %in% boot.sample) # proportion in bootstrap sample
})
mean(inbag)
#> [1] 0.634
```

Let \(w_{b,i} = 1\) if observation \(i\) is OOB in the \(b\)-th tree and zero otherwise. Further, if we let \(B_i = \sum_{b=1}^B w_{b,i}\) be the number of trees in the forest for which observation \(i\) is OOB, then the OOB prediction for the \(i\)-th training observation is given by

\(\hat{y}_i^{OOB} = \frac{1}{B_i} \sum_{b:w_{b,i}=1} \hat{y}_i^b, i = 1, 2, \dots, N.\) (7.2)

The OOB error estimate is just the error computed from these OOB predictions. (See [Hastie et al., 2009, Sec. 7.11] for a more general discussion on using the bootstrap to estimate prediction error and its apparent bias.)

To illustrate, I'm going to compute the OOB RMSE for the CRF I previously fit to the Ames housing data. There are numerous ways in which this can be
