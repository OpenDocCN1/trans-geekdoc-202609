
Result: We have a lot of correct predictions. We have 1491 correct predictions of customers that don't leave the bank and 218 of customers that leave the bank.

```
Confusion Matrix :
[1491 104]
[187 218]

Accuracy = 0.8545%
Accuracy using k-fold-cross-validation: 85.29%
Standard Deviation from k-fold-cross-validation: 1.16%
```

And then we have 104 + 187 incorrect predictions. The accuracy is (1709/2000) = 0.8545, i.e. 85.5% accuracy.
We know that's not the most relevant. The relevant accuracy we get is 85.29% from K-fold-cross-validation.
We also get 1.16% deviation. Our models' accuracy range is 84.13% to 86.45%, (85.29%+1.16%).
Besides it's very difficult to improve the accuracy because as we used before it is limited by the problem itself.

# All code at once (practiced version)

```python
# XGBoost instead of ANN

# Library
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Part 1 : Data Preprocessing
# Data Extract
dat = pd.read_csv("Churn_Modelling.csv")
x = dataset.iloc[:, 3:-1].values # this can be used too
X = dataset.iloc[:, 3:13].values # all columns from index 3, excluding 13 indexed column
y = dataset.iloc[:, 13].values # the last column

# Encode Categorical Data
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
from sklearn.compose import ColumnTransformer
# label_encoder = LabelEncoder(). "Gender" is in "3rd-column", hence X[:, 2] =
# Following is applicable to numpy array, if we used "X" = dataset.iloc[:, 3:13]
X = np.array(X) # if it is needed if X is not an Array. ie. "values" not applied
X[:, 2] = label_encoder.fit_transform(X[:, 2])
print(X)

# For a data-set we can encode it using columns "Key"
X("Gender") = label_encoder.fit_transform(X("Gender"))

# OneHotEncoder. "Geography" is in "2nd-column", hence [1]
ct = ColumnTransformer(transformers=["Encoding", OneHotEncoder(), [1]], remainder="passthrough") # remaining columns to be unchanged
X = ct.fit_transform(X)
X = np.array(X) # Convert this output to Numpy array
print(X)
X = X[:, 1:] # Excluding 0-index column to avoid dummy-variable trap

# Data Split
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
```

```python
# Part 2 : Fitting XGBoost in the training set-
from xgboost import XGBClassifier
clasifire_XGB = XGBClassifier()
clasifire_XGB.fit(X_train, y_train)
```

```python
# Part 3 : Predictions and Evaluating the model
y_pred = clasifire_XGB.predict(X_test)

# confusion matrix
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_true=y_test, y_pred=y_pred)
print(f"Confusion Matrix :\n{cm}")
# parameters of cm: y_true: Real values, y_pred: Predicted value
accuracy_By_Confusion_matrix = (cm[0][0] + cm[1][1]) / X_test.shape[0]
print(f"\nAccuracy: {accuracy_By_Confusion_matrix}%")
```

```python
# K-folds cross-validation
from sklearn.model_selection import cross_val_score
accuracies = cross_val_score(estimator=clasifire_XGB, X=X_train, y=y_train, cv=10)
mean_accu = accuracies.mean()
std_accu = accuracies.std()

print(f"\nAccuracy using k-fold-cross-validation: {:.2f}%".format(mean_accu*100))
print(f"\nStandard Deviation from k-fold-cross-validation: {:.2f}%".format(std_accu*100))
# python prctc_XGBoost.
```

# Chapter 11 : Part 3

## Deep Learning
ANN: Evaluate performance using K-fold-CV
& Hyper parameter tuning

K-fold CV or K-fold-Cross-Validation, keras-wrapper, Dropout Regularization

## 11.3.1 K-fold-CV in ANN

- K-fold CV in ANN: in the previous section we discussed K-fold-CV and applied to kernel-SVM to XGBoost. In this section we apply K-fold-CV to ANN, it is our first Deep-learning Algorithm.
- In Chapter 8: ANN, we trained our aerial neural network twice and we noticed that the accuracies are different. We want to apply K-fold-CV to evaluate Model performance accurately.
- **Variance Tradeoff**: We're trying to train a model that will not only be accurate, but also should not have too much variance of accuracy, when we train it several times.
- Previously we trained our ANN and obtained two different accuracies, 85% and 84%. When one of these two we should take to **evaluate our performance**?
- We split our data between a training-set and a test-set. It results the Variance Problem When we get the accuracy on the test set, if we run the model again and test it on another test set, we can get a very different accuracy.

So, judging our model performance only on one test set, is not the most relevant way to evaluate the model performance.

That's why we divide the training-set (or whole dataset) into equal k-groups and k-combination of (k-1)-train-group and 1-test-group, we k iterations. Finally we get a vector of accuracies for which we get the mean-accuracy and standard-deviation. It gives us a better evaluation of the model performance.

Most of time, K=10, we train our model on 9-folds and test it on the remaining fold. With 10-folds there are 10 different combinations of 9-folds-train and 1-test-fold.

- That means we can train and test the model on combinations of training and test sets. How different accuracies are.
- That will give us a much better idea of the model performance, by taking average of the differences of the accuracies and also compute the standard deviation.

We categorize the performance into 4-categories:

i. good accuracy - small variance;
ii. large accuracy - high variance;
iii. small accuracy - low variance;
iv. low accuracy - high variance

## 11.3.2 Implement K-fold CV in ANN

We implement K-fold CV after the data pre-processing phase.

- Keras wrapper: We implemented our ANN model with Keras-TensorFlow. How the K-fold-CV belongs to Scikit-learn.

Keras wrapper combines Keras and Scikit together. Keras wrapper module belongs to Keras. It will wrap K-fold cross validation by Scikit-learn, in the Keras.

```python
from keras.wrappers import KerasClassifier
from sklearn.model_selection import cross_val_score
```

![img/092657a359a0b6d8f92d657a359a0b6d](img/092657a359a0b6d8f92d657a359a0b6d)

```python
def build_ANN():
    # initialize the ANN
    ANN = Sequential()

    # "Input-layer" & "First Hidden-layer"
    ANN.add(Dense(6, activation="relu", input_dim=11))

    # "Second Hidden-layer"
    ANN.add(Dense(6, activation="relu"))

    # "Output-layer"
    ANN.add(Dense(1, activation="sigmoid"))

    # Compile the ANN
    ANN.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
    return ANN
```

We use KerasClassifier for the data pre-processing phase. The K-fold-CV belongs to Scikit-learn.

Keras wrapper combines Keras and Scikit together. Keras wrapper module belongs to Keras. It will wrap K-fold cross validation by Scikit-learn, in the Keras.

```python
from keras.wrappers import KerasClassifier
from sklearn.model_selection import cross_val_score
```

![img/092657a359a0b6d8f92d657a359a0b6d](img/092657a359a0b6d8f92d657a359a0b6d)

We use KerasClassifier for the data pre-processing phase. The K-fold-CV belongs to Scikit-learn.

Keras wrapper combines Keras and Scikit together. Keras wrapper module belongs to Keras. It will wrap K-fold cross validation by Scikit-learn, in the Keras.

```python
from keras.wrappers import KerasClassifier
from sklearn.model_selection import cross_val_score
```

![img/092657a359a0b6d8f92d657a359a0b6d](img/092657a359a0b6d8f92d657a359a0b6d)

We use KerasClassifier for the data pre-processing phase. The K-fold-CV belongs to Scikit-learn.
