permuting more than one feature at a time); this would be useful if features can be categorized into mutually exclusive groups, for instance, categorical features that have been one-hot encoded.

# 6.1.2 Software

The permutation approach to variable importance is implemented in several R packages, including: vip [Greenwell et al., 2021a], iml [Molnar and Schratz, 2020], ingredients [Biecek and Baniecki, 2021], and mnmpf [Jones, 2018]. Further details, some comparisons, and an in-depth explanation of vip are provided in Greenwell and Boehmke [2020]. Starting with version 0.22.0, scikit-learn's inspection module provides an implementation of permutation importance for any fitted model.

# 6.1.3 Example: predicting home prices

To illustrate the basic steps, let's compute permutation importance scores for the Ames housing bagged tree ensemble (ames.bag) from Section 5.5.1. I'll start by writing a simple function to compute the RMSE, the performance metric of interest, and use it to obtain a baseline value for computing the permutation-based importance scores.

```
rmse <- function(predicted, actual, na.rm = TRUE) {
  sqrt(mean((predicted - actual) ^ 2, na.rm = na.rm))
}
(baseline.rmse <- rmse(predict(ames.bag, newdata = ames.trn),
                       actual = ames.trn$Sale_Price))
```

```
#> [1] 10.6
```

To get more stable VI scores, I'll use 30 independent permutations for each predictor; since the permutations are done independently, Algorithm 6.1 can be trivially parallelized across repetitions or features. This is done using a nested for loop in the next code chunk:

```
nperm <- 30 # number of permutation to use per feature
xnames <- names(subset(ames.trn, select = -Sale_Price))
vi <- matrix(nrow = nperm, ncol = length(xnames))
colnames(vi) <- xnames
for (j in colnames(vi)) {
  for (i in seq_len(nrow(vi))) {
    temp <- ames.trn # temporary copy of training data
    temp[[j]] <- sample(temp[[j]]) # permute feature values
    pred <- predict(ames.bag, newdata = temp) # score permuted data
    permuted.rmse <- rmse(pred, actual = temp$Sale_Price) ^ 2
    vi[i, j] <- permuted.rmse - baseline.rmse # smaller is better
  }
}
```