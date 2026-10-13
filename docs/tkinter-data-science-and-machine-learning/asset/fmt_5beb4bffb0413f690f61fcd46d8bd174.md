
## True Values versus Predicted Values Diagram and Learning Curve (`plot_real_pred_val_learning_curve`)

It creates a diagram that compares the true values to the predicted values. Additionally, it plots a learning curve to illustrate how the model's performance changes with different training dataset sizes.

## Results Presentation (`shows_table`)

It loads the results of the MLP model from an Excel file named `results_MLP.csv`. This Excel file contains various performance metrics for the model. It then displays these results in a table within the GUI.

In summary, this section of the code focuses on training, evaluating, and visualizing the performance of an MLP classifier. It includes features like loading pre-trained models, conducting hyperparameter tuning with grid search, and presenting the results through various visualizations and tables.

Run `main_class.py`. Next, click on **SPLIT DATA** button. Then, choose **Multi-Layer Perceptron** to see the result of using Multi-Layer Perceptron classifier as shown in Figure 37.

![Image](images/image-7.png)

**Figure 37** The results of using Multi-Layer Perceptron classifier

Output:

```
Multi-Layer Perceptron

accuracy: 0.9043250327653998

recall: 0.9043250327653998

precision: 0.9063689747768858

f1: 0.9042095303827421

 precision recall f1-score support

 0 0.94 0.87 0.90 382

 1 0.88 0.94 0.91 381

 accuracy 0.90 763

 macro avg 0.91 0.90 0.90 763

weighted avg 0.91 0.90 0.90 763
```

The output is the performance evaluation of the Multi-Layer Perceptron (MLP) classifier. Let's break down the key metrics and their implications:

*   **Accuracy**: Accuracy measures the overall correctness of the model's predictions. In this case, the MLP classifier achieved an accuracy of approximately 90.43%. This means that about 90.43% of the test data samples were classified correctly by the model.
*   **Recall (Sensitivity)**: Recall quantifies the model's ability to correctly identify positive instances out of all actual positive instances. For the positive class (class 1), the MLP classifier achieved a recall of approximately 90.43%. This indicates that the model correctly identified around 90.43% of all actual positive cases.
*   **Precision**: Precision gauges the model's precision in correctly predicting positive instances. The MLP classifier achieved a precision of approximately 90.64% for the positive class. This means that among all instances predicted as positive, around 90.64% were indeed positive.
*   **F1-Score**: The F1-score is the harmonic mean of precision and recall, providing a balance between these two metrics. For the positive class, the MLP classifier achieved an F1-score of approximately 90.42%. A higher F1-score indicates a better balance between precision and recall.
*   **Classification Report**: The classification report provides a summary of precision, recall, and F1-score for each class (0 and 1). It also shows the support, which is the number of actual occurrences of each class in the test dataset.

Here's a conclusion based on the performance metrics:

The Multi-Layer Perceptron (MLP) classifier performed reasonably well on the test dataset, with an accuracy of approximately 90.43%. It showed a balanced performance between precision and recall, with F1-scores close to 0.90 for both classes. This suggests that the MLP classifier is effective in correctly classifying instances from both classes (0 and 1). However, further domain-specific analysis may be necessary to determine whether this level of performance meets the specific requirements of the problem at hand.

## Support Vector Classifier and Grid Search

In `Machine_Learning` class, define a new method named `support_vector()` as follows:

```python
def support_vector(self, name, X_train, X_test, y_train, y_test):
    # Support Vector Classifier
    # Define the parameter grid for the grid search
    param_grid = {
        'C': [0.1, 1, 10],
        'kernel': ['linear', 'poly', 'rbf'],
        'gamma': ['scale', 'auto', 0.1, 1],
    }
    # Initialize the SVC model
    model_svc = SVC(random_state=2021, probability=True)
    # Create GridSearchCV with the SVC model and the parameter grid
    grid_search = GridSearchCV(model_svc, param_grid, cv=3, scoring='accuracy', n_jobs=-1, refit=True)
    # Train and perform grid search
    grid_search.fit(X_train, y_train)
    # Get the best MLP Classifier model from the grid search
    best_model = grid_search.best_estimator_
    # Saves model
    joblib.dump(best_model, 'SVC_Model.pkl')
    # Print the best hyperparameters found
    print(f"Best Hyperparameters for SVC:")
    print(grid_search.best_params_)
    return best_model
```

The `support_vector()` function is for training a Support Vector Classifier (SVC) and performing hyperparameter tuning using grid search. Here's an explanation of each part of the function:

### 1. Parameter Grid Definition

You define a parameter grid `param_grid` that includes the hyperparameters to be tuned during grid search. These hyperparameters are:

*   **`C`**: This parameter controls the regularization strength. You provide a list of potential values: `[0.1, 1, 10]`.
*   **`kernel`**: The kernel function used for transforming the data. You specify three kernel options: `'linear'`, `'poly'`, and `'rbf'`.
*   **`gamma`**: This parameter defines the kernel coefficient. You provide a list of values: `['scale', 'auto', 0.1, 1]`.

### 2. SVC Model Initialization

You initialize the Support Vector Classifier (SVC) model with specific settings. You set `random_state=2021` for reproducibility and `probability=True` to enable probability estimates.

### 3. GridSearchCV Setup

You create a `GridSearchCV` object named `grid_search`. This object combines the SVC model with the parameter grid for hyperparameter tuning. It uses 3-fold cross-validation (`cv=3`), measures performance using accuracy (`scoring='accuracy'`), and utilizes all available CPU cores (`n_jobs=-1`).

### 4. Grid Search Training

You fit the `grid_search` object to the training data (`X_train` and `y_train`). This process performs an exhaustive search over the hyperparameter combinations specified in `param_grid` to find the best combination based on cross-validated accuracy.

### 5. Best Model Selection

After grid search is complete, you obtain the best SVC model (`best_model`) based on the hyperparameters that resulted in the highest cross-validated accuracy.

### 6. Model Saving

The best model is saved to a file named `SVC_Model.pkl` using the `joblib.dump()` function.

### 7. Printing Hyperparameters

You print the best hyperparameters found during the grid search.

The function returns the best trained SVC model with the selected hyperparameters.

This code demonstrates the process of hyperparameter tuning for an SVC model using grid search, helping you find the best combination of hyperparameters that optimizes the model's performance on the training data.

Then, in `Machine_Learning` class, define a new method named `implement_SVC()`:

```python
def implement_SVC(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/SVC_Model.pkl"
    if os.path.exists(file_path):
        model = joblib.load('SVC_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.support_vector(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    # Saves result into excel file
    self.obj_data.save_result(y_test, y_pred, "results_SVC.csv")
    print("Training Support Vector Classifier done...")
    return model, y_pred
```

The `implement_SVC()` function is responsible for training a Support Vector Classifier (SVC) model and performing predictions. Here's a breakdown of the function:
