
![](img/2c227bfb3620dc3d159fa5e6598afa30_218_0.png)

FIGURE 5.6: MSE for the test data from several bagged tree ensembles. The dashed lines correspond to the LASSO-based post-processed versions. Clearly, the ames.bag.6.5 ensemble benefits the most from post-processing, performing nearly on par with the standard bagged tree ensemble (ames.bag).

### 5.6 Final thoughts

Loh [2014] compared the accuracy of single decision trees to tree ensembles using both real and simulated data sets. He found that, on average, the best single-tree algorithm was about 10% less accurate than that of a tree ensemble. Nonetheless, tree ensembles will not always outperform a simpler individual tree [Loh, 2009]. These points aside, tree ensembles are a powerful class of models that are highly competitive in terms of state-of-the-art prediction accuracy. Chapters 7–8 are devoted to two powerful tree ensemble techniques.

It is also worth pointing out that while tree-based ensembles often outperform carefully tuned individual trees (like CART, CTree, and GUIDE), they are less interpretable compared to a single decision tree; hence, they are often referred to as black box models. Fortunately, post-hoc procedures exist that can help us peek into the black box to understand the relationships uncovered by the model and explain their output to others. This is the topic of Chapter 6.

## 6 Peeking inside the “black box”: post-hoc interpretability

> The lack of understanding does not hurt, as much as the lack of effort to understand does!
> Wordions

This chapter is dedicated to select topics from the increasingly popular field of *interpretable machine learning* (IML), which easily deserves its own book-length treatment, and it is so; see, for example, Molnar [2019] and Biecek and Burzykowski [2021] (both of which are freely available online). The methods covered in this chapter can be categorized into whether they help interpret a black box model at a global or local (e.g., individual row or prediction) level.

To be honest, I don’t really like the term “black box,” especially when we now have access to a rich ecosystem of interpretability tools. For example, linear regression models are often hailed as interpretable models. Sure, but this is really only true when the model has a simple form. Once you start including transformations and interaction effects—which are often required to boost accuracy and meet assumptions—the coefficients become much less interpretable.

Tree-based ensembles, especially the ones discussed in the next two chapters, can provide state-of-the-art performance, and are quite competitive with other popular supervised learning algorithms, especially on tabular data sets. Even when tree-based ensembles perform as advertised, there’s a price to be paid in terms of parsimony, as we lose the ability to summarize the model using a simple tree diagram. Luckily, there exist a number of post-hoc techniques that allow us to tease the same information out of an ensemble of trees that we would ordinarily be able to glean from looking at a simple tree diagram (e.g., which variables seem to be the most important, the effect of each predictor, and potential interactions). Note that the techniques discussed in this chapter are model-agnostic, meaning they can be applied to any type of supervised learning algorithm, not just tree-based ensembles. For example, they can also be used to help interpret neural networks or a more complicated tree structure that uses linear splits or non-constant models in the terminal nodes.

The next three sections cover post-hoc methods to help comprehend various aspects of any fitted model:

- feature importance (Section 6.1);
- feature effects (Section 6.2);
- feature contributions (Section 6.3).

### 6.1 Feature importance

For the purposes of this chapter, we can think of variable importance (VI) as the extent to which a feature has a “meaningful” impact on the predicted outcome. A more formal definition and treatment can be found in van der Laan [2006]. Given that point of view, a natural way to assess the impact of an arbitrary feature xj is to remove it from the training data and examine the drop in performance that occurs after refitting the model without it. This procedure is referred to as leave-one-covariate-out (LOCO) importance; see Hooker et al. [2019] and the references therein.

Obviously, the LOCO importance method is computationally prohibitive for larger data sets and complex fitting procedures because it requires retraining the model once more for each dropped feature. In the next section, I’ll discuss an approximate approach based on reassessing performance after randomly permuting each feature (one at a time). This procedure is referred to as permutation importance.

### 6.1.1 Permutation importance

While some algorithms, like tree-based models, have a natural way of quantifying the importance of each predictor, it is useful to have a model-agnostic procedure that can be used for any type of supervised learning algorithm. This also makes it possible to directly compare the importance of features across different types of models. In this section, I’ll discuss a popular method for measuring the importance of predictors in any supervised learning model called permutation importance.

Permutation-based VI scores exist in various forms and was made popular in Breiman [2001] for random forests (Chapter 7), before being generalized and extended in Fisher et al. [2018]. A general permutation-based VI procedure is outlined in Algorithm 6.1 below. The idea is that if we randomly permute the values of an important feature in the training data, the training performance would degrade (since permuting the values of a feature effectively destroys any relationship between that feature and the target variable). This of course assumes that the model has been properly tuned (e.g., using cross-validation) and is not overfitting.

The permutation approach uses the difference between some baseline performance measure (e.g., R^2 or RMSE for regression, Brier score or log loss for probability estimation, and AUC for discrimination) and the same performance measure obtained after permuting the values of a particular feature in the training data (Note that the model is NOT refit to the training data after randomly permuting the values of a feature). It is also important to note that this method may not be appropriate when you have, for example, highly correlated features (since permuting one feature at a time may lead to unlikely or unrealistic data instances).

**Algorithm 6.1** General steps for constructing permutation-based VI scores for any type of supervised learning model.

Let x_1, x_2, ..., x_p be the features of interest and let M_orig be the baseline performance metric for the trained model; for brevity, I'll assume smaller is better (e.g., classification error or RMSE). The permutation-based importance scores can be computed as follows:

- 1) For i = 1, 2, ..., p:
  - (a) Permute the values of feature x_i in the training data.
  - (b) Recompute the performance metric on the permuted data, denoted M_perm.
  - (c) Record the difference from baseline using VI(x_i) = M_perm - M_orig.
- 2) Return the VI scores VI(x_1), VI(x_2), ..., VI(x_j).

Algorithm 6.1 can be improved or modified in a number of ways. For instance, the process can (and should) be repeated several times and the results averaged together. This helps to provide more stable VI scores, and also the opportunity to measure their variability. Rather than taking the difference in step (c), Molnar [2019, sec. 5.5.4] argues that using the ratio M_perm/M_orig makes the importance scores more comparable across different problems. It's also possible to assign importance scores to groups of features (e.g., by permuting more than one feature at a time); this would be useful if features can be categorized into mutually exclusive groups, for instance, categorical features that have been one-hot encoded.

### 6.1.2 Software

The permutation approach to variable importance is implemented in several R packages, including: vip [Greenwell et al., 2021a], iml [Molnar and Schratz, 2020], ingredients [Biecek and Baniecki, 2021], and mnmpf [Jones, 2018]. Further details, some comparisons, and an in-depth explanation of vip are provided in Greenwell and Boehmke [2020]. Starting with version 0.22.0, scikit-learn's inspection module provides an implementation of permutation importance for any fitted model.

### 6.1.3 Example: predicting home prices

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
nperm <- 30 # number of permutations to use per feature
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
