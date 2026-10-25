
done programmatically given our setup; I chose the easy route. Recall that each tree in our rfo object contains an attribute called "oob" which stores the row numbers for the training records that were OOB for that particular tree. From these we can easily construct an N × B matrix, where the (i,j)-th element is given by

```
\begin{cases} \hat{y}_i^b & \text{if } w_{b,i} = 1 \\ \text{NA} & \text{if } w_{b,i} = 0 \end{cases}
```

The reason for using NAs in place of the predictions for the non-OOB observations will hopefully become apparent soon.

```
preds.oob <- matrix(nrow = nrow(ames.trn), ncol = B) # OOB predictions
for (b in 1:B) { # WARNING: Might take a minute or two!
  oob.rows <- attr(ames.crf[[b]], which = "oob") # OOB row IDs
  preds.oob[oob.rows, b] <-
    predict(ames.crf[[b]], newdata = ames.trn[oob.rows, ])
}

pred.oob <- rowMeans(preds.oob) # average OOB predictions across trees
```

```
# Peek at results
preds.oob[1:3, 1:6]
#>     [,1] [,2] [,3] [,4] [,5] [,6]
#> [1,] 184  NA  NA  NA  NA  163
#> [2,]  NA 143  NA  NA  NA  154
#> [3,]  NA 136 115  NA 136  NA
```

Peeking at the first few rows and columns you can see that the first training observation (which corresponds to the first row in the above matrix) was OOB in the first and sixth trees (since the rest of the columns are NA), whereas the second observation was OOB for trees two and six, so I obtain the corresponding OOB predictions for these. Next, I compute \(\hat{y}_i^{OOB}\) as in Equation (7.2) by computing the row means of our matrix pred.oob—setting na.rm = TRUE in the call to rowMeans() ensures that the NAs in the matrix aren't counted, so that the average is taken only over the OOB predictions (i.e., the correct denominator B_i will be used). Note that the OOB error is slightly larger than the test error I computed earlier; this is typical in many common settings, as noted in Janitza and Hornung [2018].

```
pred.oob <- rowMeans(preds.oob, na.rm = TRUE)
rmse(pred.oob, obs = ames.trn$Sale_Price, na.rm = TRUE)
```

```
#> [1] 26.6
```

Similar to what I did in the previous section, I can compute the OOB RMSE as a function of the number of trees in the forest. The results are displayed in Figure 7.6, along with the test RMSEs from the same forest (black curve) and test error from a single CTree fit (horizontal blue line). Here, we can see that the OOB error is consistently higher than the test error, but both begin to stabilize at around 50 trees.

```
rmse.oob <- numeric(B) # to store RMSEs
for (b in 1:B) {
  pred <- rowMeans(preds.oob[, 1:b, drop = FALSE], na.rm = TRUE)
  rmse.oob[b] <- rmse(pred, obs = ames.trn$Sale_Price, na.rm = TRUE)
}
```

![](img/2c227bfb3620dc3d159fa5e6598afa30_258_0.png)

FIGURE 7.6: RMSEs for the Ames housing example: the CRF test RMSEs (black curve), the CRF OOB RMSEs (yellow curve), and the test RMSE from a single CTree fit (horizontal blue line).

As noted in Hastie et al. [2009], the OOB error estimate is almost identical to that obtained by N-fold cross-validation, where N is the number of rows in the learning sample; this is also referred to as leave-one-out cross-validation (LOOCV). Hence, algorithms that produce OOB data can be fit in one sequence, with cross-validation being performed along the way. The OOB error can be monitored during fitting and the training can stop once the OOB error has “stabilized.” In the Ames housing example (Figure 7.6) it can be seen that the test and OOB errors both stabilize after around 50 trees.

While the OOB error is computationally cheap, Janitza and Hornung [2018] observed that it tends to overestimate the true error in many practical situations, including

- when the class frequencies are reasonably balanced in classification settings;
- when the sample size $N$ is large;
- when there is a large number of predictors;
- when there is correlation between the predictors;
- when the main effects are weak.

The positive bias of OOB error estimates was also noted in Bylander [2002]. In light of this, it seems reasonable to consider the OOB error estimate as an upper bound on the true error. Fortunately, Janitza and Hornung [2018] argue that the OOB error can be used effectively for hyperparameter tuning in RFs—which I'll discuss in the next section—without substantially affecting performance. This is good news since $k$-fold cross-validation can be computationally expensive, especially when tuning more complex models, like tree-based ensembles.

## 7.4 Hyperparameters and tuning

RF is one of the most useful *off-the-shelf* statistical learning algorithms you can know. By off-the-shelf, I mean a procedure that can be used effectively without much tweaking or tuning. Don't get me wrong, you can (and should try to) improve performance with a bit of tuning, but relative to other algorithms, the RFs often do reasonably well at their default settings. In contrast, *gradient tree boosting* (Chapter 8) can often outperform RFs, but typically require a lot more tuning.

The most important tuning parameter in an RF is $m_{try}$. But I'd argue that the typical defaults (i.e., $m_{try} = \lfloor \sqrt{p} \rfloor$ for classification and $m_{try} = \lfloor p/3 \rfloor$ for regression) are quite good. For selecting $m_{try}$, a simple heuristic is to try the default, half of the default, and twice the default, and pick the best [Liaw and Wiener, 2002]. According to Liaw and Wiener [2002], the results generally do not change dramatically, and even setting $m_{try} = 1$ can give very good performance for some data. Setting $m_{try} < p$ also lessens the computational burden of split variable selection (e.g., CART's exhaustive search for the best split), making RFs more computationally efficient than bagged tree ensembles, especially for larger data sets. On the other hand, if you only suspect a small fraction of the predictors to be “important,” then larger values of $m_{try}$ may give better generalization performance.

The number of trees in the forest ($B$) is arguably not a tuning parameter. You just need to make sure enough trees are aggregated for the error to stabilize (see, for example, Figure 7.6). However, it can be wasteful to fit more trees than necessary, especially when dealing with large data sets. For this reason, some RF implementations have the option to "stop early" if the validation error stops improving; the R package **h2o** [LeDell et al., 2021] includes an RF implementation that supports early stopping with a wide variety of performance metrics. Such early stopping can be based on an independent test set, cross-validation, or the OOB error.

What about using the OOB error estimate or tuning? Although it's been argued that the OOB error tends to overestimate the true error in certain cases (see, for example, Mitchell [2011]), Janitza and Hornung [2018] noted that the overestimation seems to have little to no impact on tuning parameter selection, at least in their simulations. If ordinary cross-validation is too expensive, and you don't have access to separate validation and test sets, then using the OOB error is a certainly reasonable thing to do, and in many cases, more efficient.

To illustrate, I carried out a small simulation using the Friedman 1 benchmark problem introduced in Section 1.4.3. For these data, there are 10 possible values for the \(m_{try}\) parameter. For each value, I generated 100 separate train and test sets of \(N = 1,000\) observations each. For each repetition, I computed the OOB and test MSE and plotted the results; the results are displayed in Figure 7.7. In this example, you can see that the OOB error is quite in line with the test error, and both suggest an optimal value of \(m_{try}\) around 5 or 6 (the traditional default here, indicated by a dashed vertical line, is \(m_{try} = \lfloor 10/3 \rfloor = 3\)).

![](img/2c227bfb3620dc3d159fa5e6598afa30_260_0.png)

FIGURE 7.7: OOB and test error vs. \(m_{try}\) for the Friedman benchmark data using \(N = 2000\) with a 50/50 split. The dashed line indicates the standard default for regression; in this case, \(m_{try} = 3\).
