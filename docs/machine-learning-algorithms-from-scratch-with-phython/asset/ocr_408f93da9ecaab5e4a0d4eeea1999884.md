```
def predict_classification(train, test_row, num_neighbors):
    neighbors = get_neighbors(train, test_row, num_neighbors)
    output_values = [row[-1] for row in neighbors]
    prediction = max(set(output_values), key=output_values.count)
    return prediction

# Test distance function
dataset = [[2.7810836,2.550537003,0],
    [1.465489372,2.362125076,0],
    [3.396561688,4.400293529,0],
    [1.38807019,1.850220317,0],
    [3.06407232,3.005305973,0],
    [7.627531214,2.759262235,1],
    [5.332441248,2.088626775,1],
    [6.922596716,1.77106367,1],
    [8.675418651,-0.242068655,1],
    [7.673756466,3.508563011,1]]
prediction = predict_classification(dataset, dataset[0], 3)
print('Expected %d, Got %d.' % (dataset[0][-1], prediction))
```

Listing 13.9: Example of Making Predictions on the Contrived Dataset.

Running this example prints the expected classification of 0 and the actual classification predicted from the 3 most similar neighbors in the dataset.

```
Expected 0, Got 0.
```

Listing 13.10: Sample Output of Making Predictions.

We can imagine how the predict_classification() function can be changed to calculate the mean value of the outcome values. Below is a quick example named predict_regression() that we will use later.

```
# Make a prediction with neighbors
def predict_regression(train, test_row, num_neighbors):
    neighbors = get_neighbors(train, test_row, num_neighbors)
    output_values = [row[-1] for row in neighbors]
    prediction = sum(output_values) / float(len(output_values))
    return prediction
```

Listing 13.11: Function To Make Regression Predictions for a New Data Row.

We now have all of the pieces to make predictions with KNN. Let's apply it to the Abalone dataset.

# 13.2.4 Abalone Case Study as Classification

In this section we will apply the k-Nearest Neighbors algorithm to the Abalone dataset. The first step is to load the dataset and convert the loaded data to numbers that we can use with the Euclidean distance calculation. For this we will use the helper function load_csv() to load the file, str_column_to_float() to convert string numbers to floats and str_column_to_int() to convert the sex column (column 0) to integer values.

We will evaluate the algorithm using k-fold cross-validation with 5 folds. This means that \(\frac{4177}{5} = 835.4\) or just over 830 records will be in each fold. We will use the helper functions