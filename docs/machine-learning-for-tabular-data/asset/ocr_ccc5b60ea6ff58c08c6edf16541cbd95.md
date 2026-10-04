you can use a fixed number of iterations based on the stopping iterations observed in cross-validation. In this case, you can calculate the average or median of all stopping points in cross-validation to determine the number of boosting trees to use. However, there's no fixed rule, and you may choose to use the second maximum value for an aggressive stopping policy or the second minimum value for a conservative one.

Additionally, consider increasing the number of boosting trees since training is done on more data during cross-validation. As a general guideline, increase the number of boosting trees by a percentage equivalent to dividing one by the number of folds used in cross-validation. However, since no one-fits-all solution exists, experimentation may be necessary to find the best approach for your problem.

As an example, we run the previous code again, this time setting a higher number of estimators to use and parameters, validation_fraction and n_iter_no_change, that activate the early stopping. The parameter validation_fraction defines the fraction of the training data to be used for validation, and it is effective only when n_iter_no_change is set to an integer indicating how many iterations should pass without improvements testing the model on the validation set before stopping the process.

# 5.11 Applying early stopping with GradientBoostingClassifier

```
model = GradientBoostingClassifier(
    n_estimators=1000,
    learning_rate=0.1,
    validation_fraction=0.2,
    n_iter_no_change=10,
    max_depth=4,
    min_samples_leaf=3,
    random_state=0
)
```

```
model_pipeline = Pipeline([
    ('column_transform', column_transform),
    ('model', model)
])
```

```
cv_scores = cross_validate(estimator=model_pipeline,
    X=data,
    y=target_median,
    scoring=accuracy,
    cv=cv,
    return_train=True,
    return_estimator=True
)
```

```
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"mean:{mean_cv:0.3f} fit:{fit_time:0.2f} secs preds:{score_time:0.2f} secs")
iters = [cv_scores['estimator'][i].named_steps["model"].n_estimators_
    for i in range(5)]
```