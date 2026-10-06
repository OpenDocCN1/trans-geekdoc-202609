+   Permutation. A form of resampling where case outcome values are shuffled (permuted) to be used in statistical tests. In more traditional statistical use, permutation tests are used to create a null distribution to calculate significance.

+   Node purity. In a terminal node, the percentage of cases that have the same observed outcome value.

+   Conditional inference forests. An alternative form of random forests that use different statistical tests to calculate variable importance.

+   Gradient. This term is often used to refer to the partial derivatives in optimization, in this chapter, the gradient refers to the residuals for each case and how these are used to create the new tree.

+   Learning rate. In gradient boosting, the learning rate refers to how fast or slow the residuals (gradient) are updated based on the predictions for each tree.

+   Partial dependency plot. An approximation of the relationship between a predictor and outcome while controlling for all other predictors. This is often used for ensemble methods given that interpretable “effects” are not generated for individual predictors.

# 6.2 Bagging

One the first proposed ensemble methods was bootstrap aggregation, or bagging (Breiman, 1996a). The algorithm proceeds in two steps. First, a bootstrap sample is taken. To create a bootstrap sample, the data are resampled with replacement and each bootstrap sample has a size equal to that of the original sample. For each bootstrap sample, a decision tree is fit using all predictor variables as potential splitting variables. Given that each bootstrap sample is different, each tree will have a unique structure manifested in the variables used, splitting values chosen, and tree size given the instability of decision trees. Once a series of decision trees are estimated, the predicted values for each person from each of the trees are output and then averaged to create the final prediction. More formally, predictions from a bagging model are created

```
$f_{bag}(x) = \frac{1}{B} \sum_{b=1}^{B} f^{b}(x)$
```