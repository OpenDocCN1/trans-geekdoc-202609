
Conda: You may use the Conda packaging manager to install XGBoost:

```bash
conda install -c conda-forge py-xgboost
```

Conda should be able to detect the existence of a GPU on your machine and install the correct variant of XGBoost. If you run into issues, try indicating the variety explicitness:

```bash
# CPU only
conda install -c conda-forge py-xgboost-cpu
```

```bash
# NVIDIA GPU
conda install -c conda-forge py-xgboost-gpu
```

## 11.2.2 XGBoost using Python: Problem description & Data-preprocessing

Problem description: This is the Churn modeling problem where we need to predict the customers of the bank that will leave the bank. We solved it using ANN in Chapter 8: Deep Learning - ANN 1 for leave and 0 for stay.

Where we classify the customers in two classes: those who leave the bank and those who will not leave the bank.
Accuracy using ANN: Remember for this problem we obtained an accuracy of 86% but that took quite a while because we trained an ANN with many epochs.

In this section we're going to use XGBoost on this Churn Modeling Problem and we're going to see that we will get the same accuracy. We'll probably better but execute in no time instantly compared to ANN.

> We cannot get a higher accuracy because the accuracy is limited by the problem itself in the sense that there isn't A 100% correlation between the informations of customers and their decision to leave the bank or not. So 86% is very close to the accuracy we can obtain for this specific business problem.

Also note: that this dataset only contains 8 features so it's not a large dataset.

It is important to note that even if we have a very large-dataset, XGBoost would be one of the best model in performance. That is to get a good accuracy and execution speed.
If you are using a large-csv I strongly encourage you to test XGBoost.

Data preprocessing: We'll do the pre-preprocessing phase from our ANN file.

Feature scaling: Using XGBoost feature-scaling is not necessary. Since XGBoost is a Gradient Boosting model with decision trees hence, features scaling is totally unnecessary.

- That's one of the very good thing about XGBoost besides its performance & high execution speed, you can keep the interpretation of your problem/data-set and the results you'll get building the model.
- High performance
- Fast execution speed.
- You can keep all the interpretation of your problem and your model (no feature-scaling).

Data-preprocessing for XGBoost

```python
# Library
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
```

```python
# Part 1 : Data Preprocessing
# Data Extract
dataset = pd.read_csv("Churn_Modelling.csv")
X = dataset.iloc[:, 1:-1] # Values what can be used to
```

```python
X = dataset.loc[:, 3:].values # all columns from index 3, excluding 3 indexed column
y = dataset.loc[:, 33].values # the last column
```

```python
# Encode Categorical Data
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
from sklearn.compose import ColumnTransformer
```

```python
# Encode "Gender" using LabelEncoder. "Gender" is in "3rd-column", hence X[:, 2]
label_encoder = LabelEncoder()
# Following is applicable to numpy array, if used X = dataset.loc[:, 3:]
# X is a numpy array so it is not an Array. i.e. .values not applied
X[:, 2] = label_encoder.fit_transform(X[:, 2])
print(X)
```

```python
# For a data-set we can still encode it using "Key"
# X["Gender"] = Label_encoder.fit_transform(X["Gender"])
# Encode "Geography" using OneHotEncoder. "Geography" is in "2nd-column"
```

```python
# Data Split
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
```

## 11.2.3 XGBoost using: Apply the model

Here are going to implement XGBoost by the classifier and creating an object of that classifier.

- We will fit this object to the training set and
- We will evaluate model performance using confusion matrix.
- We also apply K-cross-validation for evaluating the model performance

**Import the Class: use XGBClassifier for the module xgboost (we just installed it.)**

**Parameters:** When we are creating the object of XGBClassifier, we noticed that there is very little information about this when we use it (c-1 or cmd-1). **very little documentation.** The only thing we are left of is the parameters we can use

- **Some parameters:** learning_rate is in deep learning). **n_estimators (the number of estimator, xgboost) is actually a Gradient Boosting Algorithm with Trees.** The number of estimators is actually quite and then we have many other parameters but we're not going to play with those parameters now.

```python
XGBClassifier
Definition XGBClassifier(max_depth=3, learning_rate=0.1, n_estimators=100, eval_metric=None, objective='binary:logistic', min_child_weight=1, gamma=0, subsample=0.8, colsample_bytree=0.8, reg_alpha=0, reg_lambda=1, scale_pos_weight=1, base_score=0, seed=None)
Type: Present in xgboostmodule
class XGBClassifier(XGBobject):
```

However, this is only an introduction to this course but you can find any information on the Internet.

Now we're going to input any parameters we're going to be set with the default values that we use in the XGBClassifier

- So we are going to make max_depth=3, n_estimators=100 (one hundred hundreds) and the rest is fine because we actually have a binary output.

You can also try a little practice and try to use Grid Search Parameter Tuning to find the optimal parameters for the learning_rates and n_estimators. It's exactly the same technique as we did when we implemented Grid Search in the Previous Section.

- gamma parameter that you can try to tune with grid search.

Fitting this classified to the training set: We just take classifier object and fit the training-set. Exactly the same as we implemented the other classification models

```python
# Fitting XGBoost in the training set
from xgboost import XGBClassifier
cla5_XGB = XGBClassifier()
cla5_XGB.fit(X_train, y_train)
```

Prediction, confusion matrix, k-fold-cross-validation: All are copied from previous projects. Just change the classifier name.

- We make predictions on the test-set
- We also call the confusion-matrix.
- We lastly apply k-fold-cross-validation to get relevant performance metrics to assess the performance of our XGBoost model.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_356_0.png)

The dataset contains information of customers in a bank.

- The independent variables that we selected are all independent variables from credit score to estimated salary and the dependent variable is existsvariable for leave and for stay. These are the data of the previous six months that the Bank recorded.
- We training this XGBoost model in the data so that it understands the correlations between these information like the credit score, the geography, age, the estimated salary and the decision of the customer to leave the bank and there is a classification problem.
- XGBoost will classify the customers between two classes the ones that leave and the ones that stay and our goal is to make some predictions for the future customers and predict if they are going to leave yes or no.

```python
# Part 3 : Predictions and Evaluating the model
# Predict
y_pred = cla5_XGB.predict(X_test)

# By making the confusion matrix we use the function "confusion_matrix"
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(true=y_test, y_pred=y_pred)
print("\nConfusion Matrix :\n{cm}")

# parameters of cm: True Real values, y_pred: Predicted value
Accuracy_from_confusion_matrix = [cm[0][0] + cm[1][1]]/X_test.shape[0]
print("\nAccuracy = {Accuracy_from_confusion_matrix[0]}%")
```

```python
# k-fold cross-validation
from sklearn.model_selection import cross_val_score
accuracies = cross_val_score(estimator=cla5_XGB, X=X_train, y=y_train, cv=10)
mean_acc = accuracies.mean()
std_acc = accuracies.std()

print("\nAccuracy using k-fold-cross-validation: {:.2f}%".format(mean_acc*100))
print("\nStandard Deviation from k-fold-cross-validation: {:.2f}%".format(std_acc*100))
```
