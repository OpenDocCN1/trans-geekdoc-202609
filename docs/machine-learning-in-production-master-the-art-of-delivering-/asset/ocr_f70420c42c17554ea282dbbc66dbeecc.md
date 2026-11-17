+   - Data drift
+   - Prediction drift
+   - Concept shift

# Data drift

Data drift is when the distribution or characteristics of input features change with reference to training data. It is also known as feature drift, population drift, or covariate shift. If the distribution of input data changes, then its predictions might get affected as the model is not prepared for it.

If a new category gets added to the feature post-deployment, then it may cause an error while making the prediction, as it was not there at the time of model training.

Another example could be, suppose there is a feature called **Credit Rating** in training data, and it has high weightage, which means a change in this feature may cause a major change in model output. Now, the business decided to go with Moody’s credit rating instead of S&P. This will cause a change in input data. For instance, S&P’s AA- is equivalent to Moody’s Aa3 rating.

The following equation shows that the distribution of training data does not match the distribution of reference (production) data.

Mathematically, data drift can be defined as follows:

```
P(X) ≠ Pref(X)
```

Where P(X) denotes the input data probability distribution.

# Prediction drift

As input data changes with data drift, this may cause a change in the target or prediction variable. It refers to a change in predictions over time. It is also named a prior probability shift, label drift, or unconditional class shift. This can also occur due to the removal or addition of new classes. Retraining the model can help mitigate the model degradation owing to prediction drift.

Mathematically, prediction drift can be defined as follows:

```
P(Y) ≠ Pref(Y)
```

Where P(Y) denotes the prior probability distribution of target labels.

# Concept shift

A concept shift occurs when the relationship between independent variables and dependent or target variables changes. It is also known as posterior class shift, conditional change, or real concept drift. It refers to changes in the relationship