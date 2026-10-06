# 64 Machine Learning for Biomedical Applications

parameters = {"poly_features__degree": range(1,20)}
Next we create the grid search object

```
from sklearn.model_selection import GridSearchCV
grid_search = GridSearchCV(pipeline, parameters, cv=5)

We will now find the optimal degree automatically, by calling
grid_search.fit(X_train, y_train)

The best cross-validated score obtained during the grid search can be accessed as
grid_search.best_score_
>>> 0.84
nThe model with the best hyperparameters fitted to the training data
best_model = grid_search.best_estimator_
and the optimal polynomial degree
best_model.named_steps['poly_features'].degree
>>> 2
```

Evaluate performance on the test set
We can evaluate the performance on the test set using a trained GridSearchCV object by calling its method score. It will return the score of the model with the best hyperparameter setting identified during the search and fitted to the whole dataset:
grid_search.score(X_test,y_test)
>>> 0.91

# 2.3.6 Exercises

+   1. In Sect. 2 you were given code to generate a noisy dataset and the second-order polynomial model. Write code to visualize the fitted polynomial curve and the original data. Experiment with the polynomial degree of the fit and observe how the model changes.
2. Perform cross-validation for polynomial fits of different degrees to the simulated dataset and observe how the $R^2$ score changes.
3. Load the data noisy_data.csv using pandas.2 The file contains two columns:
   - column contains zero features X;

> 2 The dataset and the skeleton code for this exercise can be obtained from github.com/MachineLearningBiomedicalApplications/notebooks.