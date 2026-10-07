such that 90% of the data will be used for training, and the rest 10% will be used for validation.

We will split the data into training and test sets using the function train_test_split() from the Scikit-Learn library:

```
from sklearn.model_selection import train_test_split
```

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.10, random_state=42)

```
print("Number of data points in the training set = %d" % (X_train.shape[0])")
```

```
print("Number of data points in the test set = %d" % (X_test.shape[0])")
```

Number of data points in the training set = 5014

Number of data points in the test set = 558

train_test_split() returns datasets. We have captured these datasets in the variables X_train, X_test, y_train, and y_test. X_train contains 90% (in our case) of the original dataset (that is, X) chosen randomly and only contains the columns corresponding to the independent variables. y_train has the corresponding values of the dependent variable in relation to the dataset X_train. X_test contains the rest of the 10% of the rows from the original dataset (that is, X) and only contains the columns corresponding to the independent variables. y_test contains the corresponding values of the dependent variable corresponding to the dataset X_test.

We will train the model using X_train and y_train.

We will test the model by making predictions using X_test.

We will measure the model's goodness by comparing the predictions made on X_test to the actual values in y_test.

# Pre-processing the data

As stated before, we must find a way to represent the text as numbers. One way to do this is by preparing Term Frequency - Inverse Document Frequency (TF-IDF) for every data point. We refer to such data as a vector of TF-IDFs. To learn more about TF-IDF, we refer to Annex 6.

However, before we create the vector of TF-IDFs, we can remove non-essential words/elements from our data.

Among the non-essential words/elements are the following: