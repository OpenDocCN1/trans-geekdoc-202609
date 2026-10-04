
## CHAPTER 5 Decisision trees and gradient boosting

The secret to obtaining a good result with random forests is to choose its few hyperparameters wisely. Though the random forest algorithm is no brain-brainer when it works with default parameters, fine-tuning it will bring better results. The first purpose of the algorithm is to reduce the variance of the estimates, and that's done by setting a high number of n_estimators. The principle is that if you have many trees, you have a distribution of results, and if the results are randomly drawn, you have an effect similar to the regression to the mean (the best prediction) due to the law of large numbers. The bootstrapping of examples and sampling of the features to be considered is usually "random draws". However, you need enough trees to have a proper regression to the mean.

You need some tests to fine-tune how many trees you build since there's always a sweet spot: after a certain number of trees, you won't obtain any improvements, and sometimes some decrements in performance will result instead. Also, setting too high number of trees to be built by the algorithm will increase your computational costs, and more time will be needed in training and inference. However no matter many trees you train, if your variance starts high with the default settings of a random forest you can do to reduce it. Here the tradeoff between variance and bias comes into play that is, you can trade some variance, implying you are overfitting the data for higher bias.

You can set a proper bias for random forests by making the following adjustments:

- Setting a lower number of features to consider when looking for the best split by setting the max_features parameter
- Setting a max number of splits per tree, which will limit its growth to a certain extent, by setting the max_depth parameter
- Setting a minimum number of examples in the terminal leaves of the tree, which will limit its growth, by setting the min_samples_leaf parameter with a number higher than 1

In the next section, we explore randomized trees (ERT), a variant of random forests that can be larger and noisier.

### 5.1.3 Resorting to randomized trees

ERT (also known as extra-trees in Scikit-learn) is a more randomized kind of random forests algorithm. The reason is the choice of candidates for splits in the ensemble's single trees. In random forests, the algorithm samples its candidates for each split and then decides on the best feature to use among the candidates. Instead, the feature to be split in ERT is not evaluated among the possible candidates but randomly chosen. Afterward, the algorithm evaluates the best split point in the randomly chosen feature. First, since the trees are even uncorrelated, there is less variance in predictions from ERT—but at the price of higher bias. Random split features have an effect on the accuracy of the predictions.

Second, ERT is more computationally efficient because it doesn't test features of but a single feature each for the best. All these characteristics make ER best suited for handling:

- High-dimensional data because it will split features faster than any decision ensemble algorithm
- Noisy data because the random feature and sample selection process can reduce the influence of noisy data points, making the model more robust to extreme values
- Imbalanced data because, due to the random feature selection, the signals from the minority subset of the data will not be systematically excluded in favor of the majority subset of the data

The following listing tests ERT by replacing the random forests in 5.4, where you built a model with the Airbnb NYC dataset to figure out if the pricing of a listing is above or the median value.

#### Listing 5.5 ERTs classifier

```python
from sklearn.ensemble import ExtraTreesClassifier

accuracy = make_scorer(accuracy_score)
c = KFold(5, shuffle=True, random_state=0)
model = ExtraTreesClassifier(n_estimators=300, min_samples_leaf=3, random_state=0)
```

> ExtraTreesClassifier with 300 estimators and a minimum number of samples at a leaf node to 3

```python
column_transformer = ColumnTransformer(
  [['categorical', categorical_onehot, low_card_categorical)],
  ['numeric', numeric_passthrough, continuous)],
  remainder='drop',
  verbose_feature_names_out=False,
  sparse_threshold=0.0)
```

A column transformer that applies different transformations to categorical and numeric features

```python
model_pipeline = Pipeline(
  ['processing', column_transform],
  ['modeling', model)])

cv_scores = cross_validate(estimator=model_pipeline,
X=data,
yy=target_median,
scoring='accuracy',
cv=cv,
return_train_score=True,
return_estimator=True)
```

A pipeline that sequentially applies column transformation and the random forests classifier model

```python
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"mean_cv:{mean_cv:.3f} ({std_cv:.0.3f})")
```

A five-fold cross-validation using the defined pipeline and calculating accuracy scores

```python
fit: {fit_time:0.2f},
pred: {score_time:0.2f} secs
```

Prints the mean and standard deviation of the accuracy scores from cross-validation

You obtain a better result than using random forests:

0.823 (0.004) fit: 4.99 secs pred: 0.42 secs

If you run this example, you will see that training to ETR is much faster than random forests, when you use the same dataset and build the same number of trees. ETR becomes an interesting alternative when your dataset is larger (more cases) and even more when it is wider (more features) it saves a lot of time picking the split since it is randomly decided. By contrast, the random forests algorithm has to look for the best feature after a selection.

The fact that splits are decided randomly is a great advantage when many collinear and noisy features are related to the target. The algorithm avoids picking the same signals as an algorithm driven by searching for the best feature that fits the target. In addition, you can see the working dynamics in feature splitting of an ETR as another way to trade variance with bias. Splitting randomly is a limitation for the algorithm and reduces the variance the resulting set of trees will be very uncorrelated.

In the next section, we complete our overview of tree-based ensembles by examining gradient boosting. This slightly different enrolling approach is often more effective for tabular data problems than bagging or random patches.

## Gradient boosting

In recent years, gradient boosting trees (GBDT) has firmly established itself as a cutting-edge method for tabular data problems, generally considered best across a wide range of problems, including multiclass classification, advertising click, and search ranking. When applied to standard tabular problems, you can expect GBDT to perform better than neural networks, support vector machines, random forests, and bagging ensembles.

Above all, GBDT's ability to handle heterogeneous features and its flexibility in the choice of loss function make it most suitable for tabular data tasks. In sum, GBDT offers the following benefits for tabular data:

- With proper hyperparameter tuning, it can achieve the best performance among all techniques.
- There is no need for scaling or other monotone transformations of the features.
- It automatically captures nonlinear relationships in the data.
- It is robust to outliers and noisy data.
- It automatically handles missing data.
- It automatically selects the best features and can report their importance.

### Gradient boosting

All these characteristics depend on how the algorithm works, combining sequences of decision trees in gradient descent optimization. In fact, gradient boosting, starting from a constant value, you add tree sequentially, each correcting the errors of the previous models in a fashion similar to gradient descent. Gradient boosting represents an evolution of the original boosting approach. In Adaboost, the algorithm fits a sequence of weak learners, any machine learning algorithm that consistently beats random guessing, to the data (for an explanation about how to choose weak learners, sees https://img.bz/KG9P). It then attributes more to correct predictions and less to correct ones. Weighting helps the algorithm focus more on the observations that are harder to predict. The process is concluded after multiple corrections by a majority vote in classification or an average of the predictions in regression.

By contrast, in gradient boosting, you rely on a double optimization: first that of the single trees strive to reduce the error on your optimization function and then the general one, involving calculating the error from the summation of the boosted model, in a form that mimics gradient descent. Since you have an optimization also on a second level, the entire ensemble procedure, gradient boosting is more versatile than the previously seen tree ensembles because it allows arbitrary loss functions to be used when calculating how the summation of the predictions of models diverges from the expected results.

Figure 5.5 visually represents how the training error decreases after adding a new tree. Each tree takes part in a gradient descent style optimization, contributing to predicting the correction of the residual errors from the previous trees.

Training error![](img/def89cc476fa39f4c54bd34e78d91674_173_0.png)

Figure 5.5 How gradient descent works with boosted trees
