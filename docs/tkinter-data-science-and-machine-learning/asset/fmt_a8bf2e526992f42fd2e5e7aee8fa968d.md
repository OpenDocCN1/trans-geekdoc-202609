
## Precision

The precision score is approximately 0.871, which means that when the model predicts the positive class, it is correct about 87.1% of the time. This metric assesses the accuracy of the model's positive class predictions.

## F1-Score

The F1-score is approximately 0.869, which is the harmonic mean of precision and recall. It provides a balance between precision and recall, making it useful for imbalanced datasets.

## Confusion Matrix

The confusion matrix shows the following:

### For the "0" class (presumably the negative class)

*   **Precision**: 0.90 (90% of predicted negatives were correct)
*   **Recall**: 0.84 (84% of actual negatives were correctly predicted)
*   **F1-Score**: 0.86 (a balance between precision and recall)

### For the "1" class (presumably the positive class)

*   **Precision**: 0.85 (85% of predicted positives were correct)
*   **Recall**: 0.90 (90% of actual positives were correctly predicted)
*   **F1-Score**: 0.87 (a balance between precision and recall)

## Summary

*   The KNN classifier performs reasonably well on the dataset, with accuracy, recall, and precision scores around 87%. This suggests that the model is effective at distinguishing between the two classes.
*   The F1-scores for both classes are also similar, indicating a good balance between precision and recall for both positive and negative classes.
*   The model appears to have slightly better performance for the "0" class in terms of precision, while it has slightly better performance for the "1" class in terms of recall.

Overall, based on the output, the K-Nearest Neighbors classifier demonstrates a satisfactory level of performance in classifying the dataset, with balanced results for both positive and negative classes. However, the specific context and requirements of the application should be considered when interpreting these results.

## Decision Trees Classifier and Grid Search

In `Machine_Learning` class, define a new method named `decision_trees()` as follows:

```python
def decision_trees(self, name, X_train, X_test, y_train, y_test):
    # Initialize the DecisionTreeClassifier model
    dt_clf = DecisionTreeClassifier(random_state=2021)

    # Define the parameter grid for the grid search
    param_grid = {
        'max_depth': np.arange(1, 51, 1),
        'criterion': ['gini', 'entropy'],
        'min_samples_split': [2, 5, 10],
        'min_samples_leaf': [1, 2, 4],
    }

    # Create GridSearchCV with the DecisionTreeClassifier model and the parameter grid
    grid_search = GridSearchCV(dt_clf, param_grid, cv=3, scoring='accuracy', n_jobs=-1)

    # Train and perform grid search
    grid_search.fit(X_train, y_train)

    # Get the best DecisionTreeClassifier model from the grid search
    best_model = grid_search.best_estimator_

    # Saves model
    joblib.dump(best_model, 'DT_Model.pkl')

    # Print the best hyperparameters found
    print(f"Best Hyperparameters for DT:")
    print(grid_search.best_params_)

    return best_model
```

The code defines a function called `decision_trees()` that trains and tunes a Decision Tree classifier using grid search for hyperparameter optimization. Let's break down the function's components and purpose:

### Function Arguments

*   `name`: A string representing the name or identifier of the classifier (used for display or documentation purposes).
*   `X_train`, `X_test`, `y_train`, `y_test`: The training and testing data split, typically feature matrices (`X_train` and `X_test`) and target vectors (`y_train` and `y_test`).

### Decision Tree Classifier Initialization

The function initializes a `DecisionTreeClassifier` with a specified random seed (`random_state=2021`).

### Parameter Grid for Grid Search

A parameter grid (`param_grid`) is defined as a dictionary that includes various hyperparameters of the Decision Tree classifier:

*   `max_depth`: A range of maximum depths for the tree.
*   `criterion`: Two possible criteria for splitting nodes, either `'gini'` or `'entropy'`.
*   `min_samples_split`: Minimum number of samples required to split an internal node.
*   `min_samples_leaf`: Minimum number of samples required to be at a leaf node.

### Grid Search Cross-Validation

*   The function utilizes `GridSearchCV` to perform hyperparameter tuning using cross-validation (`cv=3`).
*   `GridSearchCV` aims to find the combination of hyperparameters that yields the highest accuracy score on the training data.
*   The search is conducted over the specified hyperparameter grid, considering different combinations of hyperparameter values.
*   The scoring metric used for evaluation is accuracy (`'accuracy'`).

### Best Model Selection

*   After completing the grid search, the function selects the best `DecisionTreeClassifier` model based on the hyperparameters that produced the highest accuracy during cross-validation.
*   The best model is stored in the variable `best_model`.

### Model Saving

The best `DecisionTreeClassifier` model is serialized and saved to a file named `'DT_Model.pkl'` using the `joblib` library. This allows the model to be reused or deployed in the future without retraining.

### Printing Best Hyperparameters

The function prints the best hyperparameters found during the grid search, providing insight into the selected hyperparameter values.

The purpose of this function is to automate the process of training and hyperparameter tuning for a Decision Tree classifier. By conducting a grid search over a range of hyperparameters, the function helps identify the best-performing model configuration. This tuned model can then be used for classification tasks, potentially improving accuracy and predictive performance compared to default parameter settings.

Then, in `Machine_Learning` class, define a new method named `implement_DT()`:

```python
def implement_DT(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/DT_Model.pkl"

    if os.path.exists(file_path):
        model = joblib.load('DT_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.decision_trees(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)

    # Saves result into excel file
    self.obj_data.save_result(y_test, y_pred, "results_DT.csv")

    print("Training Decision Trees done...")

    return model, y_pred
```

The `implement_DT()` function is responsible for training and using a Decision Tree classifier for a binary classification task. Let's analyze its components and functionality:

### Function Arguments

*   `chosen`: A string representing the chosen classification model or identifier.
*   `X_train`, `X_test`, `y_train`, `y_test`: The training and testing data split, consisting of feature matrices (`X_train` and `X_test`) and target vectors (`y_train` and `y_test`).

### File Path Check

The function checks if a file named `'DT_Model.pkl'` exists in the current working directory (`os.getcwd()`). This file is assumed to contain a pre-trained Decision Tree model.

### Model Loading or Training

*   If the `'DT_Model.pkl'` file exists, the function loads the pre-trained model using `joblib` (`joblib.load`).
*   Otherwise, it proceeds to train a Decision Tree classifier by calling the `decision_trees()` function.
*   The result of this process is the trained model, stored in the variable `model`.

### Model Prediction

*   The function uses the trained model to make predictions on the testing data (`X_test`) by calling the `run_model()` function with `proba=True`.
*   The predicted labels or probabilities are stored in the variable `y_pred`.

### Saving Results

The true labels (`y_test`) and predicted labels (`y_pred`) are saved into an Excel file named `"results_DT.csv"` using the `save_result` method of the `obj_data` object.

### Print Confirmation

A message is printed to indicate that the training of Decision Trees is complete.

### Returning Model and Predictions
