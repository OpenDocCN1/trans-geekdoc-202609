![](bbox=[0.135, 0.105, 0.465, 0.225])

# Figure 7.28: Alpha value for the first boosting iteration

How exactly are these alpha values used? In bagging, each stump gave a 0/1 vote when predicting. When it comes time to predict with your boosted stumps, each classifier will instead give *alpha* if it thinks the row is pregnant and -*alpha* if not. For this first stump, when used on the test set, it would give 0.207 points to any customer who had not bought birth control and -0.207 points to any customer who had. The final prediction of the ensemble model is the sum of all these positive and negative alpha values.

As you'll see later, to determine the overall pregnancy prediction coming from the model, a cutoff is set for the sum of the individual stump scores. Since each stump returns either a positive or negative alpha value for its contribution to the prediction, it is customary to use 0 as the classification threshold for pregnancy; however, this can be tuned to suit your precision needs.

# Reweighting

Now that you've completed one stump, it's time to reweight the training data. To do that, you need to know which rows of data this stump gets right and which rows it gets wrong.

So in column W, label W10 as **Wrong**. In W11, you can use the `OFFSET` formula in combination with the winning stump's column index (cell X2) to look up the weighted error for the training row. `OFFSET` simply takes in an anchor cell and tells Excel how many cells to move up or down and left or right from that cell. In the second parameter, we don't want to move any rows down, so that stays as a 0. We'll move the amount of columns to the right as given by Y3. If the error is nonzero, then the stump is incorrect for that row, and Wrong is set to 1:

```
=IF(OFFSET($C$11, 0, $Y$3)>0, 1, 0)
```

This formula can be copied down to all training rows (note the absolute references).

Now, the original weights for this stump are in column C. To adjust the weights according to which rows are set to 1 in the Wrong column, boosting multiplies the original weight times *exp(alpha * Wrong)*, where *exp* is the exponential function you encountered when doing logistic regression.

If the value in the Wrong column is 0, then *exp(alpha * Wrong)* becomes 1, and the weight stays put.

If Wrong is set to 1, then *exp(alpha * Wrong)* is a value larger than 1, so the entire weight is scaled up. Label X10 as **Scale by Alpha**, and in X11, you can calculate this new weight as follows:

```
=$C$11*EXP($W$11*$Y$5)
```