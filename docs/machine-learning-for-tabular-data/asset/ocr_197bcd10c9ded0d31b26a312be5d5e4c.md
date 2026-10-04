# CHAPTER 6 Advanced feature processing methods

pipeline has a name, must address each parameter in a part of the pipeline by the name of the element in the pipeline, two underscores, and the name of the hyperparameter. For instance, in our example, XGBoost is a part of the pipeline named 'xgb.' To address the hyperparameter n_estimators of XGBoost, use the label xgb_n_estimators in your search space. The idea is to demonstrate how to optimize a model and its pipeline without testing all the possible choices influencing a model’s predictive performance.

Listing 6.13 Random search

```
from sklearn.utils.fixes import logiform
from sklearn.model_selection import KFold, RandomizedSearchCV
from sklearn.metrics import accuracy_score
from sklearn.metrics import make_scorer
from xgboost import XGBClassifier
```

```
accuracy = make_scorer(accuracy_score)
cv = KFold(5, shuffle=True, random_state=0)

xgb = XGBClassifier(booster='gtree', objective='reg:logistic')
model_pipeline = Pipeline(
    (['column', transform), ('xgb', xgb])
)

search_dict = {
    'xgb_n_estimators': np.arange(100, 2000, 100),
    'xgb_learning_rate': logiform(0.01, 1),
    'xgb_max_depth': np.arange(1, 8),
    'xgb_subsample': np.arange(0.1, 0.9, 0.05),
    'xgb_colsample_bytree': np.arange(0.1, 0.9, 0.05),
    'xgb_reg_lambda': logiform(1e-9, 100),
    'xgb_reg_alpha': logiform(1e-9, 100)
}

search_func = RandomizedSearchCV(estimator=model_pipeline,
    param_distributions=search_dict,
    n_iter=60,
    scoring=accuracy,
    n_jobs=1,
    cv=cv,
    random_state=0)

search_func.fit(X=data, y=target_median)
print(search_func.best_params)
print(search_func.best_score_)
```

Creates a pipeline that combines data processing and the XGBoost classifier

A dictionary containing various hyperparameters with their search spaces for the RandomizedSearchCV

Specifies the number of iterations for the random search

Specifies the number of parallel jobs to run for the search

Prints the best hyperparameters found by the RandomizedSearchCV

Prints the best score achieved using the best hyperparameters found during the search

After a while (the code runs for about one hour in a Google Colab instance), we get the set of best parameters and the cross-validated score: