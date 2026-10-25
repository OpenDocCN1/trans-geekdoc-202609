```
# Fit a gradient tree boosted ensemble with 500 trees
set.seed(1110) # for reproducibility
ames.bst <-
  lsboost(subset(ames.trn, select = -Sale_Price), # features only
          y = ames.trn$Sale_Price, ntree = 500, depth = 4,
          shrinkage = 0.1)
```

The test RMSE as a function of the number of trees in the ensemble is computed below using the previously defined predict() method; the results are shown in Figure 8.4 (black curve). For brevity, the code uses sapply() to essentially iterate cumulatively through the B = 500 trees and computes the test RMSE for the first tree, first two trees, etc. For comparison, the test RMSEs from a default RF are also computed and displayed in Figure 8.4 (yellow curve). In this example, the GBM slightly outperforms the RF.

```
set.seed(1128) # for reproducibility
ames.rfo <- # fit a default RF for comparison
  randomForest(subset(ames.trn, select = -Sale_Price),
               y = ames.trn$Sale_Price, ntree = 500,
               # Monitor test set performance (MSE, in this case)
               xtest = subset(ames.tst, select = -Sale_Price),
               ytest = ames.tst$Sale_Price)
```

```
# Helper function for computing RMSE
rmse <- function(pred, obs, na.rm = FALSE) {
  sqrt(mean((pred - obs)^2, na.rm = na.rm))
}
```

```
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

# ## 8.6 Interpretability

Interpreting GBMs is no different from any other nonparametric model. For example, Section 5.4 discussed how the individual tree-based importance scores (Section 2.8) can be aggregated across all the trees in an ensemble