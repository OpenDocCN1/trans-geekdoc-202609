
In [26]:

ftrsel = ftr_sel.SelectPercentile(ftr_sel.mutual_info_regression,
                                 percentile=25)
ftrsel.fit_transform(diabetes_train_ftrs,
                     diabetes_train_tgt)

print(np.array(diabetes.feature_names)[ftrsel.get_support()])

['bmi' 's4' 's5']

Very generally speaking, different feature selection metrics often give similar rankings.

## 13.1.2 Model-Based Feature Selection

So far, we’ve been selecting features based either on their stand-alone characteristics (using variance) or on their relationship with the target (using correlation or information). Correlation is nice because it tracks a linear relationship with the target. Information is nicer because it tracks any—for some definition of “any”—relationship. Still, in reality, when we select features, we are going to use them with a model. It would be nice if the features we used were tailored to that model. Not all models are lines or otherwise linear. The existence of a relationship between a feature and a target does not mean that a particular model can find or make use of it. So, we can naturally ask if there are any feature selection methods that can work with models to select features that work well in that model. The answer is yes.

A second issue, up to this point, is that we’ve only evaluated single features, not sets of features. Models work with whole sets of features in one go. For example, linear regressions have coefficients on each feature, and decision trees compare values of some features after considering all features. Since models work with multiple features, we can use the performance of models on different baskets of features to assess the value of those features to the models.

Combinatorics—the sheer number of ways of picking a subset of features from a bigger set—is what usually prevents us from testing each and every possible subset of features. There are simply too many subsets to evaluate. There are two major ways of addressing this limitation: randomness and greediness. It sounds like we are taking yet another trip to a casino.

Randomness is fairly straightforward: we take subsets of the features at random and evaluate them. Greediness involves starting from some initial set of features and adding or removing features from that starting point. Here, greed refers to the fact that we may take steps that individually look good, but we may end up in a less-than-best final spot. Think of it this way. If you are wandering around a big city without a map, looking for the zoo, you might proceed by walking to a corner and asking, “Which way to the zoo?” You get an answer and follow the directions to a next corner. If people are honest—we can hope—you might end up at the zoo after quite a long walk. Unfortunately, different people might have different ideas about how to take you to the zoo, so you might end up backtracking or going around in circles for a bit. If you had a map, however, you could take yourself there directly via a shortest path. When we have a limited view of the total problem—whether standing on a street corner or only considering some features to add or delete—we may not reach an optimal solution.

In practice, greedy feature selection gives us an overall process that looks like this:

- 1. Select some initial set of features.
- 2. Build a model with the current features.
- 3. Evaluate the importance of the features to the model.
- 4. Keep the best features or drop the worst features from the current set. Systematically or randomly add or remove features, if desired.
- 5. Repeat from step 2, if desired.

Very often, the starting point is either (1) a single feature, with us working forward by adding features, or (2) all the features, with us working backward by removing features.

### 13.1.2.1 Good for Model, Good for Prediction

Without the repetition step (step 5), we only have a single model-building step. Many models give their input features an importance score or a coefficient. SelectFromModel uses these to rank and select features. For several models, the default is to keep the features with the score above the mean or average.

In [27]:

ftrsel = ftr_sel.SelectFromModel(ensemble.RandomForestClassifier(),
                                    threshold='mean') # default
ftrsel.fit_transform(wine_train, wine_train_tgt)
print(np.array(wine.feature_names)[ftrsel.get_support()])

['alcohol' 'flavanoids' 'color_intensity' 'hue' 'od280/od315_of_diluted_wines' 'proline']

For models with L₁ regularization—that's what we called the lasso in Section 9.1—the default threshold is to throw out small coefficients.

In [28]:

lmlr = linear_model.LogisticRegression
ftrsel = ftr_sel.SelectFromModel(lmlr(penalty='l1'))
    # thresh is "small" coeffs
ftrsel.fit_transform(wine_train, wine_train_tgt)

print(np.array(wine.feature_names)[ftrsel.get_support()])

['alcohol' 'malic_acid' 'ash' 'alcalinity_of_ash' 'magnesium' 'flavanoids' 'proanthocyanins' 'color_intensity' 'od280/od315_of_diluted_wines' 'proline']

Note that we don’t have any easy way to order the selected features unless we go back to the coefficients or importances from the underlying model. SelectFromModel gives us a binary—yes or no—look at whether to keep features or not.

### 13.1.2.2 Let a Model Guide Decision

Going beyond a one-step process, we can let the basket of features grow or shrink based on repeated model-building steps. Here, the repetition of step 5 (from two sections back) is desired. Imagine we build a model, evaluate the features, and then drop the worst feature. Now, we repeat the process. Since features can interact with each other, the entire ordering of the features may now be different. We drop the worst feature under the new ordering. We continue on until we’ve dropped as many features as we want to drop. This method is called recursive feature elimination and is available in sklearn through RFE.

Here we will use a RandomForestClassifier as the underlying model. As we saw in Section 12.3, random forests (RFs) operate by repeatedly working with random selections of the features. If a feature shows up in many of the component trees, we can use that as an indicator that a more frequently used feature has more importance than a less frequently used feature. This idea is formalized as the feature importance.

In [29]:

```
```python
ftrsel = ftr_sel.RFE(ensemble.RandomForestClassifier(),
                    n_features_to_select=5)

res = ftrsel.fit_transform(wine_train, wine_train_tgt)
print(np.array(wine.feature_names)[ftrsel.get_support()])
```
```

['alcohol' 'flavanoids' 'color_intensity' 'od280/od315_of_diluted_wines' 'proline']

We can also select features using a linear regression model. In the sklearn implementation, features are dropped based on the size of their regression coefficients. Statisticians should now read a warning in the End-of-Chapter Notes.

In [30]:

```
```python
# statisticians be warned (see end-of-chapter notes)
# this picks based on feature weights (coefficients)
# not on significance of coeffs nor on r^2/anova/F of (whole) model
ftrsel = ftr_sel.RFE(linear_model.LinearRegression(),
                    n_features_to_select=5)
ftrsel.fit_transform(wine_train, wine_train_tgt)
print(np.array(wine.feature_names)[ftrsel.get_support()])
```
```

['alcohol' 'total_phenols' 'flavanoids' 'hue' 'od280/od315_of_diluted_wines']

We can use .ranking_ to order the dropped features—that is, where in the rounds of evaluation they were kept or dropped—without going back to the coefficients or importances of the models that were used along the way. If we want to order the remaining features—the keepers—we have to do some extra work:

In [31]:

```
# all the 1s are selected; non-1s indicate when they were dropped
# go to the estimator and ask its coefficients
print(ftrsel.ranking_,
      ftrsel.estimator_.coef_, sep='\n')
```

[1 5 2 4 9 1 1 3 7 6 1 1 8]
[-0.2164  0.1281 -0.3936 -0.6394 -0.3572]

Here, the 1s in the ranking are selected: they are our keepers. The non-1s indicate when that feature was dropped. The five 1s can be ordered based on the the absolute value of the five estimator coefficients.

In [32]:

```
# the order for the five 1s
keepers_idx = np.argsort(np.abs(ftrsel.estimator_.coef_))
# find the indexes of the 1s and get their ordering
keepers_order_idx = np.where(ftrsel.ranking_ == 1)[0][keepers_idx]
print(np.array(wine.feature_names)[keepers_order_idx])
```

['total_phenols' 'alcohol' 'od280/od315_of_diluted_wines' 'flavanoids' 'hue']

## 13.1.3 Integrating Feature Selection with a Learning Pipeline

Now that we have some feature selection tools to play with, we can put together feature selection and model building in a pipeline and see how various combinations do. Here's a quick baseline of regularized logistic regression on the wine data:

In [33]:

```
skms.cross_val_score(linear_model.LogisticRegression(),
                     wine.data, wine.target)
```

Out[33]:

array([0.8667, 0.95 , 1.    ])

You might wonder if selecting features based on that same classifier helps matters:
