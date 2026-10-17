

```python
return dataset_split

# test cross validation split
seed(1)
dataset = [[1], [2], [3], [4], [5], [6], [7], [8], [9], [10]]
folds = cross_validation_split(dataset, 4)
print(folds)
```

Listing 3.5: Example of a Cross-Validation Split of a Contrived Dataset.

Running the example produces the output below. The list of the folds is printed, showing that indeed as expected there are two rows per fold.

```text
[[[2], [9]], [[8], [3]], [[5], [6]], [[7], [10]]]
```

Listing 3.6: Example Output from Creating a Cross-Validation Split.

### 3.2.3 How to Choose a Resampling Method

The gold standard for estimating the performance of machine learning algorithms on new data is *k*-fold cross-validation. When well-configured, *k*-fold cross-validation gives a robust estimate of performance compared to other methods such as the train and test split. The downside of cross-validation is that it can be time-consuming to run, requiring *k* different models to be trained and evaluated. This is a problem if you have a very large dataset or if you are evaluating a model that takes a long time to train.

The train and test split resampling method is the most widely used. This is because it is easy to understand and implement, and because it gives a quick estimate of algorithm performance. Only a single model is constructed and evaluated. Although the train and test split method can give a noisy or unreliable estimate of the performance of a model on new data, this becomes less of a problem if you have a very large dataset.

Large datasets are those in the hundreds of thousands or millions of records, large enough that splitting it in half results in two datasets that have nearly equivalent statistical properties. In such cases, there may be little need to use *k*-fold cross-validation as an evaluation of the algorithm and a train and test split may be just as reliable.

### 3.3 Extensions

In this tutorial, we have looked at the two most common resampling methods. There are other methods you may want to investigate and implement as extensions to this tutorial. For example:

- **Repeated Train and Test.** This is where the train and test split is used, but the process is repeated many times.
- **LOOCV or Leave One Out Cross-Validation.** This is a form of *k*-fold cross-validation where the value of *k* is fixed at 1.
- **Stratification.** In classification problems, this is where the balance of class values in each group is forced to match the original dataset.

### 3.4 Review

In this tutorial, you discovered how to implement resampling methods in Python from scratch. Specifically, you learned:

- How to implement the train and test split method.
- How to implement the *k*-fold cross-validation method.
- When to use each method.

### 3.4.1 Further Reading

- Section 9.6, Generate pseudorandom numbers, *The Python Standard Library*  
  https://docs.python.org/2/library/random.html
- Section 5.1. Cross Validation, page 176, *An Introduction to Statistical Learning*, 2014.  
  http://amzn.to/2eeTyQx
- Section 18.4. Evaluating and Choosing the Best Hypothesis, page 708, *Artificial Intelligence: A Modern Approach*, 2010.  
  http://amzn.to/2e31FqP
- Section 4.4 Resampling Techniques, page 69, *Applied Predictive Modeling*, 2013  
  http://amzn.to/2e31NXF
- Section 5.3, Cross-validation, page 149, *Data Mining: Practical Machine Learning Tools and Techniques*, second edition, 2005.  
  http://amzn.to/2fj3SYY

### 3.4.2 Next

In the next tutorial, you will discover how to evaluate the predictions made by predictive modeling algorithms.

## Chapter 4 Evaluation Metrics

After you make predictions, you need to know if they are any good. There are standard measures that we can use to summarize how good a set of predictions actually is. Knowing how good a set of predictions is allows you to make estimates about the skill of a given machine learning model of your problem. In this tutorial, you will discover how to implement four standard prediction evaluation metrics from scratch in Python.

After reading this tutorial, you will know:

- How to implement classification accuracy.
- How to implement and interpret a confusion matrix.
- How to implement mean absolute error for regression.
- How to implement root mean squared error for regression.

Let’s get started.

### 4.1 Description

You must estimate the quality of a set of predictions when training a machine learning model. Performance metrics like classification accuracy and root mean squared error can give you a clear objective idea of how good a set of predictions is, and in turn how good the model is that generated them. This is important as it allows you to tell the difference and select among:

- Different transforms of the data used to train the same machine learning model.
- Different machine learning models trained on the same data.
- Different configurations for a machine learning model trained on the same data.

As such, performance metrics are a required building block in implementing machine learning algorithms from scratch.

| 1 | 1 |
|---|---|

Listing 4.2: Example of a Set of Contrived Predictions and Expected Values.

Below is a complete example with this dataset to test the accuracy_metric() function.

```python
# Example of calculating classification accuracy

# Calculate accuracy percentage between two lists
def accuracy_metric(actual, predicted):
    correct = 0
    for i in range(len(actual)):
        if actual[i] == predicted[i]:
            correct += 1
    return correct / float(len(actual)) * 100.0

# Test accuracy
actual = [0,0,0,0,0,1,1,1,1,1]
predicted = [0,1,0,0,0,1,0,1,1,1]
accuracy = accuracy_metric(actual, predicted)
print(accuracy)
```

Listing 4.3: Example of Calculating Classification Accuracy.

Running this example produces the expected accuracy of 80% or 8/10.

| 80.0 |
|------|

Listing 4.4: Example Output From Calculating Classification Accuracy.

Accuracy is a good metric to use when you have a small number of class values, such as 2, also called a binary classification problem. Accuracy starts to lose its meaning when you have more class values and you may need to review a different perspective on the results, such as a confusion matrix.

### 4.2.2 Confusion Matrix

A confusion matrix provides a summary of all of the predictions made compared to the expected actual values. The results are presented in a matrix with counts in each cell. The counts of predicted class values are summarized horizontally (rows), whereas the counts of actual values for each class values are presented vertically (columns). A perfect set of predictions is shown as a diagonal line from the top left to the bottom right of the matrix.

The value of a confusion matrix for classification problems is that you can clearly see which predictions were wrong and the type of mistake that was made. Let's create a function to calculate a confusion matrix.

We can start off by defining the function to calculate the confusion matrix given a list of actual class values and a list of predictions. The function is listed below and is named confusion_matrix(). It first makes a list of all of the unique class values and assigns each class value a unique integer or index into the confusion matrix.

The confusion matrix is always square, with the number of class values indicating the number of rows and columns required. Here, the first index into the matrix is the row for actual values and the second is the column for predicted values. After the square confusion matrix is created and initialized to zero counts in each cell, it is a matter of looping through all predictions and

```python
# Test confusion matrix with integers
actual = [0,0,0,0,0,1,1,1,1,1,1]
predicted = [0,1,1,0,0,1,0,0,1,1,1]
unique, matrix = confusion_matrix(actual, predicted)
print(unique)
print(matrix)
```

Listing 4.7: Example of Calculating a Confusion Matrix.

Running the example produces the output below. The example first prints the list of unique values and then the confusion matrix.

```text
set([0, 1])
[[3, 1], [2, 4]]
```

Listing 4.8: Example Output From Calculating a Confusion Matrix.

It’s hard to interpret the results this way. It would help if we could display the matrix as intended with rows and columns. Below is a function to correctly display the matrix. The function is named `print_confusion_matrix()`. It names the columns as Z for Actual and the rows as P for Predicted. Each column and row are named for the class value to which it corresponds.

The matrix is laid out with the expectation that each class label is a single character or single digit integer and that the counts are also single digit integers. You could extend it to handle large class labels or prediction counts as an exercise.

```python
# pretty print a confusion matrix
def print_confusion_matrix(unique, matrix):
    print('(^)' + ' '.join(str(x) for x in unique))
    print('(-)')
    for i, x in enumerate(unique):
        print("%s| %s" % (x, ' '.join(str(x) for x in matrix[i])))
```

Listing 4.9: Function To Pretty Print a Confusion Matrix.

We can piece together all of the functions and display a human readable confusion matrix

```python
# Example of Calculating and Displaying a Pretty Confusion Matrix

# calculate a confusion matrix
def confusion_matrix(actual, predicted):
    unique = set(actual)
    matrix = [list() for x in range(len(unique))]
    for i in range(len(unique)):
        matrix[i] = [0 for x in range(len(unique))]
    lookup = dict()
    for i, value in enumerate(unique):
        lookup[value] = i
    for i in range(len(actual)):
        x = lookup[actual[i]]
        y = lookup[predicted[i]]
        matrix[y][x] += 1
    return unique, matrix

# pretty print a confusion matrix
def print_confusion_matrix(unique, matrix):
    print('(^)' + ' '.join(str(x) for x in unique))
```

