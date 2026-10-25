the call to `glmnet()`. Second, since the individual tree predictions are all on the same scale, there's no need to standardize the inputs (`standardize = FALSE`). Lastly, we could argue that the estimated coefficients (one for each tree) should be non-negative (`lower.limits = 0`).

Figure 5.5 shows the regularization path for the estimated coefficients. In particular, the \(\lambda\) values (on the log scale) are plotted on the \(x\)-axis, and the \(y\)-axis corresponds to the estimated coefficient value (one curve per coefficient/tree). The top axis highlights the number of non-zero coefficients at each particular value of the penalty parameter \(\lambda\):

![](bbox=[0.18, 0.32, 0.88, 0.57])

FIGURE 5.5: Profiles of LASSO coefficients for the `ames.bag.6.5` ensemble, as the regularization parameter \(\lambda\) is varied. The top axis indicates the number of non-zero coefficients at a particular value of \(\lambda\) (plotted on the log scale).

From here, we use cross-validation or an independent test set to choose a reasonable value of the penalty parameter \(\lambda\). This can be done easily using `glmnet`'s `assess.glmnet()` function with the test set predictions using, as shown below (see `?glmnet::assess.glmnet` for details):

```
# Assess performance of fit using an independent test set
perf <- assess.glmnet(
  object = lasso.ames.bag, # fitted LASSO model
  newx = preds.tst, # test predictions from individual trees
  newy = ames.tst$Sale_Price, #same response variable (test set)
  family = "gaussian" # for MSE and MAE metrics
)
perf <- do.call(cbind, args = perf) # bind results into matrix
```