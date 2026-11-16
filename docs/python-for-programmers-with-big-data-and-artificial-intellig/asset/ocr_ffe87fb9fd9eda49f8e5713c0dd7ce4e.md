```
In [15]: X_test.shape
Out[15]: (450, 64)
```

To specify _different_ splits, you can set the sizes of the testing and training sets with the train_test_split function's keyword arguments test_size and train_size. Use floating-point values from 0.0 through 1.0 to specify the percentages of the data to use for each. You can use integer values to set the precise numbers of samples. If you specify one of these keyword arguments, the other is inferred. For example, the statement

lick here to view code image

```
X_train, X_test, y_train, y_test = train_test_split(
    digits.data, digits.target, random_state=11, test_size=0.20)
```

specifies that 20% of the data is for testing, so train_size is inferred to be 0.80.

# ## 14.2.5 Creating the Model

The **KNeighborsClassifier** estimator (module _sklearn.neighbors_) implements the k-nearest neighbors algorithm. First, we create the KNeighborsClassifier estimator object:

lick here to view code image

```
In [16]: from sklearn.neighbors import KNeighborsClassifier
In [17]: knn = KNeighborsClassifier()
```

To create an estimator, you simply create an object. The internal details of how this object implements the k-nearest neighbors algorithm are hidden in the object. You'll simply call its methods. This is the essence of Python _object-based programming_.

# ## 14.2.6 Training the Model

Next, we invoke the KNeighborsClassifier object's _fit method_, which loads the sample training set (X_train) and target training set (y_train) into the estimator:

lick here to view code image