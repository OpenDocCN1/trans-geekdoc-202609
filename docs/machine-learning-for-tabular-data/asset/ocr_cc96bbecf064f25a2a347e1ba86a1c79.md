# CHAPTER 5 Decision trees and gradient boosting

```
ffit: {fit_time:0.2f),
secs pred: (score_time:0.2f) secs
```

Prints the mean and standard deviation of the accuracy scores from cross-validation

You obtain a better result than using random forests:

0.823 (0.004) fit: 4.99 secs pred: 0.42 secs

If you run this example, you will see that training to ETR is much faster than random forests, when you use the same dataset and build the same number of trees. ETR becomes an interesting alternative when your dataset is larger (more cases) and even more when it is wider (more features) it saves a lot of time picking the split since it is randomly decided. By contrast, the random forests algorithm has to look for the best feature after a selection.

The fact that splits are decided randomly is a great advantage when many collinear and noisy features are related to the target. The algorithm avoids picking the same signals as an algorithm driven by searching for the best feature that fits the target. In addition, you can see the working dynamics in feature splitting of an ETR as another way to trade variance with bias. Splitting randomly is a limitation for the algorithm and reduces the variance the resulting set of trees will be very uncorrelated.

In the next section, we complete our overview of tree-based ensembles by examining gradient boosting. This slightly different enrolling approach is often more effective for tabular data problems than bagging or random patches.

# Gradient boosting

In recent years, gradient boosting decision trees (GBDT) has firmly established itself as a cutting-edge method for tabular data problems. GBDT is generally considered a state-of-the-art learning method across a wide range of problems multiple domains, including multiclass classification, advertising click prediction, and search engine ranking. When applied to standard tabular problems, you can expect GBDT to perform better than neural networks, support vector machines, random forests, and bagging ensembles.

Above all, GBDT's ability to handle heterogeneous features and its flexibility in the choice of the loss function and evaluation metrics make the algorithm most suitable for tabular data predictive modeling tasks. In sum, GBDT offers the following benefits for tabular data problems:

+   * With proper hyperparameter tuning, it can achieve the best performance among all other techniques.
* There is no need for scaling or other monotone transformations of the features.
* It automatically captures nonlinear relationships in the data.
* It is robust to outliers and noisy data.
* It automatically handles missing data.
* It automatically selects the best features and can report their importance.