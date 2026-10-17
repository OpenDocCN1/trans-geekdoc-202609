
return 1.0 if activation >= 0.0 else 0.0
```

Listing 10.1: Function To Make Predictions with Perceptron Weights.

We can contrive a small dataset to test our prediction function.

| X1 | X2 | Y |
|---|---|---|
| 2.7810836 | 2.550537003 | 0 |
| 1.465489372 | 2.362125076 | 0 |
| 3.396561688 | 4.400293529 | 0 |
| 1.38807019 | 1.850220317 | 0 |
| 3.06407232 | 3.005305973 | 0 |
| 7.627531214 | 2.759262235 | 1 |
| 5.332441248 | 2.088626775 | 1 |
| 6.922596716 | 1.77106367 | 1 |
| 8.675418651 | -0.242068655 | 1 |
| 7.673756466 | 3.508563011 | 1 |

Listing 10.2: Small Contrived Dataset for Testing Logistic Regression.

Below is a plot of the dataset using different colors to show the different classes for each point.

![](img/eb4f6b07d6861add2c4caceda6f4837f_94_0.png)

Figure 10.1: Plot of the Small Contrived Dataset for Testing the Perceptron algorithm.

We can also use previously prepared weights to make predictions for this dataset. Putting this all together we can test our `predict()` function below.

```
# Example of making predictions

# Make a prediction with weights
def predict(row, weights):
    activation = weights[0]
    for i in range(len(row)-1):
        activation += weights[i + 1] * row[i]
    return 1.0 if activation >= 0.0 else 0.0
```

```
# test predictions
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
weights = [-0.1, 0.20653640140000007, -0.23418117710000003]
for row in dataset:
    prediction = predict(row, weights)
    print("Expected=%d, Predicted=%d" % (row[-1], prediction))
```

Listing 10.3: Example of Making Predictions on the Contrived Dataset.

There are two inputs values (X1 and X2) and three weight values (bias, w1 and w2). The activation equation we have modeled for this problem is:

activation = (w1 × X1) + (w2 × X2) + bias (10.4)

Or, with the specific weight values we chose by hand as:

activation = (0.206 × X1) + (-0.234 × X2) + -0.1 (10.5)

Running this function we get predictions that match the expected output (y) values.

```
Expected=0, Predicted=0
Expected=0, Predicted=0
Expected=0, Predicted=0
Expected=0, Predicted=0
Expected=0, Predicted=0
Expected=1, Predicted=1
Expected=1, Predicted=1
Expected=1, Predicted=1
Expected=1, Predicted=1
Expected=1, Predicted=1
```

Listing 10.4: Example Output From Making Predictions on the Contrived Dataset.

Now we are ready to implement stochastic gradient descent to optimize our weight values.

## 10.2.2 Training Network Weights

We can estimate the weight values for our training data using stochastic gradient descent. Stochastic gradient descent requires two parameters:

- Learning Rate: Used to limit the amount each weight is corrected each time it is updated.
- Epochs: The number of times to run through the training data while updating the weight.

These, along with the training data will be the arguments to the function. There are 3 loops we need to perform in the function:

- 1. Loop over each epoch.
- 2. Loop over each row in the training data for an epoch.
- 3. Loop over each weight and update it for a row in an epoch.

As you can see, we update each weight for each row in the training data, each epoch. Weights are updated based on the error the model made. The error is calculated as the difference between the expected output value and the prediction made with the candidate weights.

There is one weight for each input attribute, and these are updated in a consistent way. For example:

$w(t + 1) = w(t) + \text{learning rate} \times (expected(t) - predicted(t)) \times x(t)$ (10.6)

The bias is updated in a similar way, except without an input as it is not associated with a specific input value:

$bias(t + 1) = bias(t) + \text{learning rate} \times (expected(t) - predicted(t))$ (10.7)

Now we can put all of this together. Below is a function named `train_weights()` that calculates weight values for a training dataset using stochastic gradient descent.

```python
# Estimate Perceptron weights using stochastic gradient descent
def train_weights(train, l_rate, n_epoch):
	weights = [0.0 for i in range(len(train[0]))]
	for epoch in range(n_epoch):
		sum_error = 0.0
		for row in train:
			prediction = predict(row, weights)
			error = row[-1] - prediction
			sum_error += error**2
			weights[0] = weights[0] + l_rate * error
			for i in range(len(row)-1):
				weights[i + 1] = weights[i + 1] + l_rate * error * row[i]
		print('>epoch=%d, lrate=%.3f, error=%.3f' % (epoch, l_rate, sum_error))
	return weights
```

Listing 10.5: Function To Estimate Weights for the Perceptron.

You can see that we also keep track of the sum of the squared error (a positive value) each epoch so that we can print out a nice message each outer loop. We can test this function on the same small contrived dataset from above.

```python
# Example of training weights

# Make a prediction with weights
def predict(row, weights):
	activation = weights[0]
	for i in range(len(row)-1):
		activation += weights[i + 1] * row[i]
	return 1.0 if activation >= 0.0 else 0.0

# Estimate Perceptron weights using stochastic gradient descent
def train_weights(train, l_rate, n_epoch):
	weights = [0.0 for i in range(len(train[0]))]
	for epoch in range(n_epoch):
		sum_error = 0.0
		for row in train:
			prediction = predict(row, weights)
			error = row[-1] - prediction
			sum_error += error**2
			weights[0] = weights[0] + l_rate * error
			for i in range(len(row)-1):
				weights[i + 1] = weights[i + 1] + l_rate * error * row[i]
		print('>epoch=%d, lrate=%.3f, error=%.3f' % (epoch, l_rate, sum_error))
	return weights

# Calculate weights
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
l_rate = 0.1
n_epoch = 5
weights = train_weights(dataset, l_rate, n_epoch)
print(weights)
```

Listing 10.6: Example of Estimating Weights on the Contrived Dataset.

We use a learning rate of 0.1 and train the model for only 5 epochs, or 5 exposures of the weights to the entire training dataset. Running the example prints a message each epoch with the sum squared error for that epoch and the final set of weights.

```
>epoch=0, lrate=0.100, error=2.000
>epoch=1, lrate=0.100, error=1.000
>epoch=2, lrate=0.100, error=0.000
>epoch=3, lrate=0.100, error=0.000
>epoch=4, lrate=0.100, error=0.000
[-0.1, 0.20653640140000007, -0.23418117710000003]
```

Listing 10.7: Example Output From Estimating Weights on the Contrived Dataset.

You can see how the problem is learned very quickly by the algorithm. Now, let's apply this algorithm on a real dataset.

## 10.2.3 Sonar Case Study

In this section, we will train a Perceptron model using stochastic gradient descent on the Sonar dataset. The example assumes that a CSV copy of the dataset is in the current working directory with the file name sonar.all-data.csv. The dataset is first loaded, the string values converted to numeric and the output column is converted from strings to the integer values of 0 to 1. This is achieved with helper functions load_csv(), str_column_to_float() and str_column_to_int() to load and prepare the dataset.

We will use k-fold cross-validation to estimate the performance of the learned model on unseen data. This means that we will construct and evaluate k models and estimate the performance as the mean model error. Classification accuracy will be used to evaluate each model. These behaviors are provided in the cross_validation_split(), accuracy_metric() and evaluate_algorithm() helper functions.

We will use the predict() and train_weights() functions created above to train the model and a new perceptron() function to tie them together. Below is the complete example.

```python
# Perceptron Algorithm on the Sonar Dataset
from random import seed
from random import randrange
from csv import reader

# Load a CSV file
def load_csv(filename):
    dataset = list()
    with open(filename, 'r') as file:
        csv_reader = reader(file)
        for row in csv_reader:
            if not row:
                continue
            dataset.append(row)
    return dataset

# Convert string column to float
def str_column_to_float(dataset, column):
    for row in dataset:
        row[column] = float(row[column].strip())

# Convert string column to integer
def str_column_to_int(dataset, column):
    class_values = [row[column] for row in dataset]
    unique = set(class_values)
    lookup = dict()
    for i, value in enumerate(unique):
        lookup[value] = i
    for row in dataset:
        row[column] = lookup[row[column]]
    return lookup

# Split a dataset into k folds
def cross_validation_split(dataset, n_folds):
    dataset_split = list()
    dataset_copy = list(dataset)
    fold_size = int(len(dataset) / n_folds)
    for _ in range(n_folds):
        fold = list()
        while len(fold) < fold_size:
            index = randrange(len(dataset_copy))
            fold.append(dataset_copy.pop(index))
        dataset_split.append(fold)
    return dataset_split

# Calculate accuracy percentage
def accuracy_metric(actual, predicted):
```
