Conda: You may use the Conda packaging manager to install XGBoost:

```
```bash
conda install -c conda-forge py-xgboost
```
```

Conda should be able to detect the existence of a GPU on your machine and install the correct variant of XGBoost. If you run into issues, try indicating the variety explicitness:

```
```bash
# CPU only
conda install -c conda-forge py-xgboost-cpu
```
```

```
```bash
# NVIDIA GPU
conda install -c conda-forge py-xgboost-gpu
```
```

# 11.2.2 XGBoost using Python: Problem description & Data-preprocessing

Problem description: This is the Churn modeling problem where we need to predict the customers of the bank that will leave the bank. We solved it using ANN in Chapter 8: Deep Learning - ANN 1 for leave and 0 for stay.

Where we classify the customers in two classes: those who leave the bank and those who will not leave the bank.
Accuracy using ANN: Remember for this problem we obtained an accuracy of 86% but that took quite a while because we trained an ANN with many epochs.

In this section we're going to use XGBoost on this Churn Modeling Problem and we're going to see that we will get the same accuracy. We'll probably better but execute in no time instantly compared to ANN.

> We cannot get a higher accuracy because the accuracy is limited by the problem itself in the sense that there isn't A 100% correlation between the informations of customers and their decision to leave the bank or not. So 86% is very close to the accuracy we can obtain for this specific business problem.

Also note: that this dataset only contains E features so it's not a large dataset.

It is important to note that even if we have a very large-dataset, XGBoost would be one of the best model in performance. That is to get a good accuracy and execution speed.
If you are using a large-csv I strongly encourage you to test XGBoost.

Data preprocessing: We'll do the pre preprocessing phase from our ANN file.

Feature scaling: Using XGBoost feature-scaling is not necessary. Since XGBoost is a Gradient Boosting model with decision trees hence, features scaling is totally unnecessary.

+   That's one of the very good thing about XGBoost besides its performance & high execution speed, you can keep the interpretation of your problem/data-set and the results you'll get building the model.

+   - High performance
- Fast execution speed.
- You can keep all the interpretation of your problem and your model (no feature-scaling).

Data-preprocessing for XGBoost

```
```python
# Library
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
```
```

```
```python
# Part 1 : Data Preprocessing
# Data Extract
dataset = pd.read_csv("Churn_Modelling.csv")
X = dataset.iloc[:, 1:-1] # Values what can be used to
```
```