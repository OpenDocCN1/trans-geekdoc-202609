# CHAPTER 6 Advanced feature processing methods

are from Scikit-learn or not. Just notice how the name of the hyperparameters are formulated in the model_name_of_the_hyperparameter because we are optimizing a pipeline and addressing parameters that are first internal to the pipeline and then of them. We will come back to this in the next subsection with more explanations.

# Listing 6.12 Grid search

```
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score
from sklearn.model_selection import KFold, GridSearchCVCV
from sklearn.metrics import make_scorer
```

```
accuracy = make_scorer(accuracy_score)
cv = KFold(5, shuffle=True, random_state=0)
model = LogisticRegression(solver='sagas', max_iter=5000)
```

```
model_pipeline = Pipeline(
    ('processing', lm_column_transform),
    ('model', model)
)
```

```
search_grid = {
    'model_penalty': [None],
    'model_penalty': ['l1', 'l2'], 'model_C': np.linspace(-4, 4, 10),
    'model_penalty': ['elasticnet'], 'model_C': np.linspace(-4, 4, 10),
    'model_l1_ratio': [.1, .3, .5, .7, .9, .99]
}
```

A list of dictionaries specifying a search grid of hyperparameters for the logistic regression model

```
search_func = GridSearchCV(estimator=model_pipeline,
                             param_grid=search_grid,
                             scoring='accuracy',
                             cv=cv)
```

Initializes a GridSearchCV object using the defined search grid

```
search_func.fit(X, y=target_median)
print (search_func.best_params_)
print (search_func.best_score_)
```

Prints the best hyperparameters found by the search grid

Prints the best score achieved by the model using the best hyperparameters found during the search grid

After all combinations, the grid search confirms that the best set of hyperparameters is not to use any penalty at all. It returns the best cross-validated score in support of its report:

```
'model_penalty': None
0.8210860006135597
```

Grid search is effective when your hyperparameters are few; they take discrete values, and you can parallelize in memory the testing operations because your dataset is not too large.

First, the more combinations, the more you have to take to the grid and more computations you will have to spend. It could be a serious problem if you need to