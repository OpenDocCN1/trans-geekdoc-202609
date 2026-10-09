The LTE lasso and related approaches can give you point estimates of the treatment effects, but they don't come with the nice *inferential* properties (i.e., standard errors) that you get from OLS. In **Chapter 3**, we introduced the parametric bootstrap and subsampling as methods for uncertainty quantification after model selection, and it is possible to adapt versions of those algorithms for use in treatment effect estimation. However, in the context of the LTE model, there is a nice alternative algorithm for inference: sample splitting.

In a sample splitting algorithm, you split the sample into, say, two pieces. You do model selection on one piece and then, conditional upon that selected model, do standard inference on the second piece. For example, with a linear lasso you could apply OLS (i.e., fit the MLE) in the second stage using only those covariates that had a nonzero selected coefficient in the first-stage lasso regression.

Recall the hockey example from **Chapter 3**. For every goal, coded as $y = 1$ for home-team goals and $y = 0$ for away-team goals, we regressed $y$ onto indicators for the teams, for the game scenarios (e.g., power plays), and for which players were present on the ice. These indicators were signed according to home versus away teams so that, for example, a home player on the ice for goal $i$ has $x_{ij} = 1$ and an away team player on the ice has $x_{ij} = -1$ (and those off the ice are all zeros). We then built a big lasso regression that predicted, given who is on the ice, which team scored every goal.

> Unlike the original analysis of **Chapter 3**, here we will penalize everything (including team and on-ice scenario coefficients). This is just to keep the example simple; you could also use sample splitting with the former specification.

To do inference via sample splitting, we first fit a regression model to half of the data:

```
```r
> library(gamlr)
> data(hockey) # load the data
> x <- cBind(config, team, player)
> y <- goal$homegoal
> fold <- sample.int(2, nrow(x), replace=TRUE)
> nhlprereg <- gamlr(x[fold==1,], y[fold==1],
+   family= "binomial", standardize=FALSE)
```
```