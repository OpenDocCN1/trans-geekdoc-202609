The tuned model is stored in grid.best_estimator_. We will now evaluate performance
of this model on the test set:

```
y_pred_test = grid.best_estimator_.predict(X_test)
RMSE = np.sqrt(mean_squared_error(y_pred_test,y_test))
```

The indices of the selected features can be accessed

```
selector = grid.best_estimator_named_steps['selector']
selector.get_support(indices=True)
```

# 8.2.6 Interpretation of machine learning models

An added benefit of feature selection is that we learn which features are informative for
ourour prediction task. In our simulated example (Fig. 8.6), the highly predictive low-noise
features 1 and 2 were selected by all the methods. In addition, the nonlinear feature 3
was selected by techniques that can deal with nonlinearity (mutual information, random
forest). The feature 4 contained only noise was never selected.

However, we need to be careful in cases when we have highly correlated features in
our dataset. In this case the feature–selection methods might select one representative
feature and discard the other correlated features even if they are highly predictive, par-
ticular, if we use lasso or recursive feature elimination. Let’s now compare top-ranking
features selected from 86 brain structure volumes using different selection techniques.
To do that, we will first load the names of the labels for the 86 brain structures and
write a function that list the selected structures:

```
names = pd.read_csv('labels', header=None, sep='\t')
```

```
def PrintFeatureNames(labels):
    for i in range(labels.size):
        print(names.loc[i],1])
```

Now, we will check the four features that have highest correlation with age at
scan y:

```
selector = SelectKBest(f_regression, k=4)
X_selected = selector.fit_transform(X, y)
ind = selector.get_support(indices=True)
PrintFeatureNames(ind)
>>> Frontal lobe right GM
>>> Frontal lobe left GM
>>> Parietal lobe right GM
>>> Parietal lobe left GM
```

Next let’s apply model based selection using Lasso: