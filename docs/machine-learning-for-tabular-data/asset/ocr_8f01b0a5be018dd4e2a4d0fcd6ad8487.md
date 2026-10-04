# Introduction to LightGBM

parameter replaces n_estimators. The following listing shows an example of the HistGradientBoostingClassifier applied to our classification problem with the Airbnb NYC dataset classification listings over the median market value.

# Listing 5.18 The new Scikit-learn's histogram gradient boosting

```
from sklearn.ensemble import HistGradientBoostingClassifier
from sklearn.metrics import accuracy_score
```

```
accuracy = make_scorer(accuracy_score)
cv = KFold(5, shuffle=True, random_state=0)
```

```
model = HistGradientBoostingClassifier(learning_rate=0.1,
max_iter=300,
max_depth=4,
min_samples_leaf=3,
random_state=0)
```

```
model_pipeline = Pipeline([
  ('processing', column_transform),
  ('modeling', model)])
```

```
cv_scores = cross_validate(estimator_pipeline,
X=data,
y=target_median,
scoring=accuracy,
cv=cv,
return_train_score=True,
return_estimator=estimator)
```

```
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"mean cv: {mean_cv:.3f} (std cv: {std_cv:.3f})")
print(f"fit_time: {fit_time:.2f}")
print(f"secs pred: {score_time:.2f} secs")
```

The results are

0.827 (0.005) fit: 1.71 secs pred: 0.13 secs

Compared to previous examples with XGBoost and LightGBM, this one differs from the used command and the max_iter parameter in exchange for the usual n_estimators. Also, the Scikit-learn new boosting algorithm is a histogram one. You just set the max_bins argument to change the default value of 255 (it is 256 bins because 1 is reserved for missing cases).

The algorithm is still under development and lacks support for sparse data. This implies that it cannot perform as fast as XGBoost in the presence of many one-hot encoded features, no matter how you prepare your data.