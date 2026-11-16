We first break the data into a training set and a testing set to prepare to train and test the model. The function train_test_split from the sklearn.model_selection module shuffles the data to randomize it, then splits the samples in the data array and the target values in the target array into training and testing sets. This helps ensure that the training and testing sets have similar characteristics. The shuffling and splitting is performed conveniently for you by a ShuffleSplit object from the sklearn.model_selection module. Function train_test_split returns a tuple of four elements in which the first two are the samples split into training and testing sets, and the last two are the corresponding target values split into training and testing sets. By convention, uppercase X is used to represent the samples, and lowercase y is used to represent the target values:

lick here to view code image

```
In [12]: from sklearn.model_selection import train_test_split

In [13]: X_train, X_test, y_train, y_test = train_test_split(
   ...:     digits.data, digits.target, random_state=11)
   ...:

```

We assume the data has balanced classes—that is, the samples are divided evenly among the classes. This is the case for each of scikit-learn's bundled classification datasets. Unbalanced classes could lead to incorrect results.

In the “Functions” chapter, you saw how to seed a random-number generator for reproducibility. In machine-learning studies, this helps others confirm your results by working with the same randomly selected data. Function train_test_split provides the keyword argument random_state for reproducibility. When you run the code in the future with the same seed value, train_test_split will select the same data for the training set and the same data for the testing set. We chose the seed value (11) arbitrarily.

# Training and Testing Set Sizes

Looking at X_train’s and X_test’s shapes, you can see that, by default, train_test_split reserves 75% of the data for training and 25% for testing:

lick here to view code image

```
In [14]: X_train.shape

Out[14]: (1347, 64)
```