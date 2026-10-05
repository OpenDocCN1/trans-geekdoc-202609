y_tr:
[1 0 0 0 0]

Next, we train the model on the training data. There are several parameters that can be set, such as the maximum number of iterations, but the default settings will be used here. To turn off the penalty for large parameter values, we include penalty='none'.

```
model = LogisticRegression(penalty='none').fit(x_tr, y_tr)
```

We can produce the predicted probability of each class by calling the predict_proba() function. Here are the probabilities for the first five subjects in the training set:

```
model.predict_proba(x_tr)[:5,:]
```

OUTPUT

```
array([[0.00893677, 0.99106323],
[0.00135816, 0.99864184],
[0.95568155, 0.04431845],
[0.7259018, 0.2740912 ],
[0.93858145, 0.06141853]])
```

For each row, the values are the probabilities that the tumor is benign (negative-class) and malignant, respectively. For example, for the first subject, the probability of a benign cell is 0.00893677, and the probability of the malignant cell is 0.99106323. Since the malignant probability is greater than the default threshold of 0.5, the predicted cell type is 1 (malignant).

Suppose we want to change the threshold and predict malignancy if the probability of the positive-label is greater than 0.85. The threshold adjustment can be done like this:

```
model.predict_proba(x_tr)[:,] > 0.85
```

This will compute the predicted probabilities for each subject and compare the positive-label probabilities against the threshold for each subject. Since we need to be more confident in predicting malignancy, we can expect the precision to be higher (fewer false positives) but the recall to be lower (more false negatives).

The sklearn package allows easily training the model, but it abstracts away the mathematics. To dive deeper, we will make the connection between what the code is doing and how the sigmoid function works. We can extract the parameter estimates for the intercept and slopes, and apply the sigmoid function to calculate the probability of malignancy for a sample patient.