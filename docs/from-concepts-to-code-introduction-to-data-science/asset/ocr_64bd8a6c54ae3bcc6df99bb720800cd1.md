An Overview of Machine Learning

Earlier, we reviewed a evaluation scheme where we split the data into train/validation/test. We discussed the training data on the training set, tuning on the validation set, and evaluating the model on the test set after all decisions were made.

A thorough way to evaluate model performance is *k-fold cross validation*. The idea is to break the data into *k* equal pieces and take turns evaluating model performance on each of them. Figure 12.4 illustrates the procedure for a typical value of *k = 5*. For each iteration, 4/5 of the data is randomly assigned to the validation set and 1/5 is randomly assigned to the validation set. The portion of data in the validation set is different for each iteration. The model is trained on the training data, and a metric such as MSE is computed on the validation data. This results in 5 measurements of MSE (one for each validation set), and they are averaged for an overall MSE.

| Iteration | Fold 1 | Fold 2 | Fold 3 | Fold 4 | Fold 5 | MSE |
|---|---|---|---|---|---|-|
| Iteration 1 | validation | train | train | train | train | MSE1 |
| Iteration 2 | train | validation | train | train | train | MSE2 |
| Iteration 3 | train | train | validation | train | train | MSE3 |
| Iteration 4 | train | train | train | validation | train | MSE4 |
| Iteration 5 | train | train | train | train | validation | MSE5 |

FIGURE 12.4: K-Fold Cross Validation Illustration

K-fold cross validation is a best practice for model evaluation and hyperparameter tuning, but it can be expensive. From our earlier example with 15 combinations of hyperparameters, considering running 10-fold cross validation. Each combination will require fitting and evaluating 10 models, for a total of 150 models. For a massive dataset, it might be sufficient to use $k = 5$ or even $k = 3$.

The `sklearn` module provides functionality for grid search through the `GridSearchCV` function. One of the important inputs is the grid containing hyperparameters. Here is a small example:

```
from sklearn.model_selection import GridSearchCV
from sklearn.linear_model import LogisticRegression
```

```
grid = {'C': [0.01, 0.1, 10], 'penalty': ['l1', 'l2']}
model = LogisticRegression()
model_cv = GridSearchCV(model, grid, cv=10)
model_cv.fit(xtrain, ytrain)
```

The grid is a dictionary containing two hyperparameters: 'C' and 'penalty'. A logistic regression model$^2$ is instantiated, and the model, the grid, and a splitting strategy parameter 'cv' are passed to the `GridSearchCV` object.

$2$We will study logistic regression in detail later.