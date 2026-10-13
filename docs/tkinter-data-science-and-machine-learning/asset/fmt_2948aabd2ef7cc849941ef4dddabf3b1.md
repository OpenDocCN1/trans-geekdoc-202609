
# Get the best Logistic Regression model from the grid search

```python
best_model = grid_search.best_estimator_
```

# Saves model

```python
joblib.dump(best_model, 'LR_Model.pkl')
```

# Print the best hyperparameters found

```python
print(f"Best Hyperparameters for LR:")
print(grid_search.best_params_)
```

```python
return best_model
```

The `logistic_regression()` method in the `Machine_Learning` class is responsible for training a Logistic Regression classifier using hyperparameter tuning through grid search. Here's a step-by-step explanation of the method:

## 1. Method Arguments

*   `name`: A string representing the name or identifier for the model being trained (e.g., "Logistic Regression").
*   `X_train`: The feature matrix of the training data.
*   `X_test`: The feature matrix of the testing data.
*   `y_train`: The target labels of the training data.
*   `y_test`: The target labels of the testing data.

## 2. Grid Search for Hyperparameter Tuning

A parameter grid (`param_grid`) is defined, specifying a range of hyperparameters for the Logistic Regression classifier. This includes different values for the regularization strength (`C`), penalty type (`penalty`), and solver method (`solver`).

## 3. Logistic Regression Model Initialization

A Logistic Regression classifier (`logreg`) is initialized with some configuration, including a maximum number of iterations and a random seed. The `max_iter` parameter is set to 5000 to ensure that the solver converges, and `random_state` is set to 2021 for reproducibility.

## 4. Grid Search with Cross-Validation

`GridSearchCV` is used to perform grid search with cross-validation. It takes the initialized Logistic Regression model (`logreg`), the parameter grid (`param_grid`), the number of cross-validation folds (`cv=3`), the scoring metric (`scoring='accuracy'`), and the option to parallelize the search (`n_jobs=-1`).

## 5. Training and Model Selection

The `fit()` method of the grid search object (`grid_search`) is called with the training data (`X_train`, `y_train`) to train multiple Logistic Regression models with different hyperparameter combinations.

## 6. Best Model Selection

The best-performing Logistic Regression model with the optimal hyperparameters is obtained using `grid_search.best_estimator_`.

## 7. Model Saving

The best-performing Logistic Regression model is saved to a pickle file named `LR_Model.pkl` using the `joblib.dump` method. This allows the model to be reused later without retraining.

## 8. Printing Best Hyperparameters

The method prints the best hyperparameters found during the grid search for the Logistic Regression classifier.

## 9. Return Value

The best-performing Logistic Regression model is returned as the output of the method.

Overall, this method automates the process of hyperparameter tuning for a Logistic Regression classifier, ensuring that the model is trained with the best hyperparameters found during the grid search.

Then, in `Machine_Learning` class, define a new method named `implement_LR()` as follows:

```python
def implement_LR(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/LR_Model.pkl"
    if os.path.exists(file_path):
        model = joblib.load('LR_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.logistic_regression(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    # Saves result into excel file
    self.obj_data.save_result(y_test, y_pred, "results_LR.csv")
    print("Training Logistic Regression done...")
    return model, y_pred
```

The `implement_LR()` method in the `Machine_Learning` class is responsible for implementing the Logistic Regression classifier for a given dataset and chosen category (target variable). Here's a step-by-step explanation of the method:

## 1. Method Arguments

*   `chosen`: A string representing the chosen category or target variable.
*   `X_train`: The feature matrix of the training data.
*   `X_test`: The feature matrix of the testing data.
*   `y_train`: The target labels of the training data.
*   `y_test`: The target labels of the testing data.

## 2. Checking for Pre-trained Model

The method checks if a pre-trained Logistic Regression model exists in the current working directory. This is done by constructing the file path to `LR_Model.pkl` and using `os.path.exists(file_path)`.

## 3. Model Loading or Training

*   If a pre-trained model exists, it is loaded using `joblib.load('LR_Model.pkl')`. Otherwise, the `logistic_regression` method is called to train a new Logistic Regression model with hyperparameter tuning.
*   Whether the model is loaded or trained, it is stored in the `model` variable.

## 4. Model Evaluation and Prediction

*   The `run_model()` method is called to evaluate the model's performance on the testing data (`X_test`, `y_test`). The `proba` parameter is set to `True`, indicating that probability scores for class predictions should be computed.
*   The predicted class probabilities or labels are stored in the `y_pred` variable.

## 5. Saving Model Results

The method uses the `save_result()` method from the `Process_Data` class (`self.obj_data`) to save the model's results, including actual and predicted labels, into an Excel file named `results_LR.csv`.

## 6. Printing Status

A message is printed to indicate that the training or loading of the Logistic Regression model is complete.

## 7. Return Value

The trained or loaded Logistic Regression model (`model`) and the predicted class probabilities or labels (`y_pred`) are returned as output.

Overall, this method allows you to either load a pre-trained Logistic Regression model or train a new one based on the chosen category, and then evaluates its performance on the testing data while saving the results for further analysis.

Then, in `Helper_Plot` class, define a new method named `choose_plot_ML()` method as follows:

```python
def choose_plot_ML(self, root, chosen, X_train, X_test, y_train, y_test, figure1, canvas1, figure2, canvas2):
    if chosen == "Logistic Regression":
        best_model, y_pred = self.obj_ml.implement_LR(chosen, X_train, X_test, y_train, y_test)
        # Plots confusion matrix and ROC
        self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
        # Plots true values versus predicted values diagram and learning curve
        self.plot_real_pred_val_learning_curve(best_model, X_train, y_train,
                                               X_test, y_test, y_pred, chosen, figure2, canvas2)
        # Shows table of result
        df_lr = self.obj_data.read_dataset("results_LR.csv")
        self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of Logistic Regression")
```

The `choose_plot_ML()` method is responsible for selecting and displaying specific plots and visualizations related to a chosen machine learning algorithm. Below is a breakdown of how this method works:

## 1. Method Arguments

*   `root`: The root Tkinter window where the plots and tables will be displayed.
*   `chosen`: A string representing the chosen machine learning algorithm.
*   `X_train`: The feature matrix of the training data.
*   `X_test`: The feature matrix of the testing data.
*   `y_train`: The target labels of the training data.
*   `y_test`: The target labels of the testing data.
*   `figure1`: A Matplotlib figure object for the first set of plots.
*   `canvas1`: A Matplotlib canvas object associated with `figure1`.
*   `figure2`: A Matplotlib figure object for the second set of plots.
*   `canvas2`: A Matplotlib canvas object associated with `figure2`.

## 2. Conditional Block Based on the Chosen Algorithm

The method checks the value of the `chosen` variable to determine which machine learning algorithm has been selected.

## 3. Logistic Regression (Chosen Algorithm)
