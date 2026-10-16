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

# 13.1.3 Integrating Feature Selection with a Learning Pipeline

Now that we have some feature selection tools to play with, we can put together feature selection and model building in a pipeline and see how various combinations do. Here's a quick baseline of regularized logistic regression on the wine data:

In [33]:

```
skms.cross_val_score(linear_model.LogisticRegression(),
                     wine.data, wine.target)
```

Out[33]:

array([0.8667, 0.95 , 1.    ])

You might wonder if selecting features based on that same classifier helps matters: