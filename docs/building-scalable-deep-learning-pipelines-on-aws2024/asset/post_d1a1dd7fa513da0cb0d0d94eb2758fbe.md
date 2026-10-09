
- epochs (int): Number of epochs (iterations over the entire dataset) for training. The default is set to 100.
- batch_size (int): Number of samples processed per gradient update. The default is set to 32.

Returns:
- None

### Model Architecture
- The method initializes a sequential model (Sequential), which is a linear stack of layers. Four dense layers are added to the model with different configurations:
    - The first layer (Dense(64, activation='relu', input_shape=self.input_shape)) has 64 units with the ReLU activation function and takes the input shape defined by the number of features.
    - The subsequent layers (Dense(32, activation='relu'), Dense(16, activation='relu')) have 32 and 16 units, respectively, both with the ReLU activation function.
    - The last layer (Dense(1)) has a single unit, representing the output layer.

### Compilation
- The model is compiled using the Adam optimizer (optimizer='adam') and the Mean Squared Error loss function (loss='mse').

### Training
- The compiled model is trained (self.model.fit) using the training features and labels. The training process runs for the specified number of epochs (epochs) and uses the specified batch size (batch_size).

### Hyperparameter Selection
- Epochs: The choice of 100 epochs was made based on common practices in neural network training, providing a balance between learning the data patterns and avoiding overfitting. While no extensive experimentation was conducted, 100 epochs is a reasonable starting point that typically allows the model to converge.
- Batch Size: A batch size of 32 was selected as it is a widely accepted standard that balances computational efficiency and model accuracy. It is a commonly used default that works well in most cases, offering a good trade-off between training speed and generalization.

## Step 6: evaluate_model Method Definition

In this step, we create the evaluate_model method, within the TSLARegressor class, which is responsible for evaluating the trained neural network model using test data:

```python
[In]: def evaluate_model(self, test_features, test_labels):
    """
    Evaluate the trained model.
    
    Parameters:
    - test_features (ndarray): Test features.
    - test_labels (ndarray): Test labels.
    
    Returns:
    - float: Test loss.
    """
    test_loss = self.model.evaluate(test_features, test_labels)
    return test_loss
```

The evaluate_model method evaluates the trained neural network model by computing the loss on the test data.

Here’s an explanation of the method’s parameters and what it does:

### Parameters
- test_features (ndarray): NumPy array containing the test features
- test_labels (ndarray): NumPy array containing the corresponding test labels

### Returns
- float: Test loss, indicating how well the model performs on the test data

### Evaluation
- The method uses the evaluate function of the trained model (self.model) to compute the loss on the test data.
- It passes the test features and labels to the evaluate function, which calculates the loss based on the model’s predictions and the true labels.

### Test Loss
- The computed test loss is returned as the output of the method. This value provides insight into the model’s performance on unseen data. A lower test loss indicates better performance, as it signifies that the model’s predictions are closer to the true labels.

## Step 7: predict_and_evaluate Method Definition

In this step, we create the predict_and_evaluate method, which serves the purpose of predicting values using the trained neural network model and then evaluating its performance based on R-squared score:

```python
[In]: def predict_and_evaluate(self, test_features, test_labels):
        """
        Predict and evaluate the neural network model.
        
        Parameters:
            - test_features (ndarray): Test features.
            - test_labels (ndarray): Test labels.
            
        Returns:
            - float: R2 score.
        """
        test_predictions = self.model.predict(test_features)
        r2_score_value = r2_score(test_labels, test_predictions)
        return r2_score_value
```

This method predicts values using the trained neural network model (self.model) on the test features and evaluates its performance using the R-squared score.

Let's break down the method's parameters and functionality:

### Parameters
- test_features (ndarray): NumPy array containing the test features
- test_labels (ndarray): NumPy array containing the corresponding test labels

### Returns
- float: R-squared score, which measures the proportion of the variance in the dependent variable (test labels) that is predictable from the independent variable (test features) in the model

### Prediction
- The method first predicts values for the test features using the predict function of the trained model (self.model).
- The predictions are stored in the variable test_predictions.

### Evaluation (R-squared Score)
- The method then calculates the R-squared score by comparing the predicted values (test_predictions) with the true test labels (test_labels).
- The r2_score function from the Scikit-Learn library is used for this purpose.

### R-squared Score Calculation
- R-squared score indicates the proportion of the variance in the dependent variable that is predictable from the independent variable.
- A higher R-squared score (closer to 1) indicates that a larger proportion of the variance in the dependent variable is predictable from the independent variable, suggesting a better fit of the model to the data.
- The computed R-squared score is returned as the output of the method, providing a measure of the model's predictive performance on the test data.

## Step 8: plot_actual_vs_predicted Function Definition

We are now outside the TSLARegressor class. We create the plot_actual_vs_predicted function, which plots the actual vs. predicted values of the test data using Matplotlib:

```python
[In]: def plot_actual_vs_predicted(tsla_regressor, test_features, test_labels):
    """
    Plot actual vs. predicted values.

    Parameters:
      - tsla_regressor (TSLARegressor):
        Instance of TSLARegressor class.
      - test_features (ndarray): Test features.
      - test_labels (ndarray): Test labels.

    Returns:
      - None
    """
    test_predictions = tsla_regressor.model.predict(test_features)

    print("Actual    Predicted")
    for actual, predicted in zip(test_labels, test_predictions):
        print(f"{actual:.2f}  {predicted[0]:.2f}")

    plt.figure(figsize=(10, 6))
    plt.scatter(test_labels, test_predictions, color='blue')
    plt.plot(
        [test_labels.min(), test_labels.max()],
        [test_labels.min(), test_labels.max()],
        'k--', lw=3
    )
    plt.xlabel('Actual')
    plt.ylabel('Predicted')
    plt.title('Actual vs. Predicted Values')
    plt.show()
```

Let's break down what the function accomplishes:

### Parameters
- tsla_regressor (TSLARegressor): An instance of the TSLARegressor class, containing the trained neural network model (model)
- test_features (ndarray): NumPy array containing the test features
- test_labels (ndarray): NumPy array containing the corresponding test labels

### Returns
- None

### Predictions
- The function first predicts the values of the test features using the trained neural network model (tsla_regressor.model.predict(test_features)).
- The predicted values are stored in the variable test_predictions.

### Printing Actual vs. Predicted Values
- The function prints the actual and predicted values side by side for comparison.
- It iterates over each pair of actual and predicted values using a loop and prints them formatted to two decimal places.

### Plotting Actual vs. Predicted Values
- The function creates a scatter plot to visualize the relationship between the actual and predicted values.
- The actual values are plotted on the x-axis (test_labels), and the predicted values are plotted on the y-axis (test_predictions).
- Additionally, a diagonal dashed line is plotted to represent the ideal scenario where actual and predicted values are identical.

### Plot Customization
- The function customizes the plot by setting labels for the x-axis and y-axis and providing a title.
- The plot is displayed using plt.show().

### Visualization
- This visualization allows for a visual assessment of how well the model’s predictions align with the actual values.
- A tight clustering of points along the diagonal dashed line indicates a strong correlation between actual and predicted values, suggesting good model performance.
