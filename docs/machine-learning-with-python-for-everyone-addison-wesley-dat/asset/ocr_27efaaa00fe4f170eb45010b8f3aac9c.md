Note that we don’t have any easy way to order the selected features unless we go back to the coefficients or importances from the underlying model. SelectFromModel gives us a binary—yes or no—look at whether to keep features or not.

# 13.1.2.2 Let a Model Guide Decision

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