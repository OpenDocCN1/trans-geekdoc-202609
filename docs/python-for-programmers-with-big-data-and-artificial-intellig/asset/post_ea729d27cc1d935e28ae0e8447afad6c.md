
were classified as the digit 0, and none of the test samples were misclassified as any of the digits 1 through 9. So 100% of the 0s were correctly predicted.

On the other hand, consider row 8 which represents the results for the digit 8:

Click here to view code image

```
[ 0, 1, 1, 2, 0, 0, 0, 0, 39, 1]
```

- The 1 at column index 1 indicates that one 8 was incorrectly classified as a 1.
- The 1 at column index 2 indicates that one 8 was incorrectly classified as a 2.
- The 2 at column index 3 indicates that two 8s were incorrectly classified as 3s.
- The 39 at column index 8 indicates that 39 8s were correctly classified as 8s.
- The 1 at column index 9 indicates that one 8 was incorrectly classified as a 9.

So the algorithm correctly predicted 88.63% (39 of 44) of the 8s. Earlier we saw that the overall prediction accuracy of this estimator was 97.78%. The lower prediction accuracy for 8s indicates that they’re apparently harder to recognize than the other digits.

## Classification Report

The sklearn.metrics module also provides function classification_report, which produces a table of classification metrics 5 based on the expected and predicted values:

5 http://scikit-learn.org/stable/modules/model_evaluation.html#precision-recall-nd-f-measures.

Click here to view code image

```
In [29]: from sklearn.metrics import classification_report
In [30]: names = [str(digit) for digit in digits.target_names]
In [31]: print(classification_report(expected, predicted,
...: target_names=names))
```

| | precision | recall | f1-score | support |
|---|---|---|---|---|
| 0 | 1.00 | 1.00 | 1.00 | 45 |
| 1 | 0.98 | 1.00 | 0.99 | 45 |
| 2 | 0.98 | 1.00 | 0.99 | 54 |
| 3 | 0.95 | 0.95 | 0.95 | 44 |
| 4 | 0.98 | 0.98 | 0.98 | 50 |
| 5 | 0.97 | 1.00 | 0.99 | 38 |
| 6 | 1.00 | 1.00 | 1.00 | 42 |
| 7 | 0.96 | 1.00 | 0.98 | 45 |
| 8 | 0.97 | 0.89 | 0.93 | 44 |
| 9 | 0.98 | 0.95 | 0.96 | 43 |
| micro avg | 0.98 | 0.98 | 0.98 | 450 |
| macro avg | 0.98 | 0.98 | 0.98 | 450 |
| weighted avg | 0.98 | 0.98 | 0.98 | 450 |

In the report:

- **precision** is the total number of correct predictions for a given digit divided by the total number of predictions for that digit. You can confirm the precision by looking at each column in the confusion matrix. For example, if you look at column index 7, you’ll see 1s in rows 3 and 4, indicating that one 3 and one 4 were incorrectly classified as 7s and a 45 in row 7 indicating the 45 images were correctly classified as 7s. So the _precision_ for the digit 7 is 45/47 or 0.96.

- **recall** is the total number of correct predictions for a given digit divided by the total number of samples that should have been predicted as that digit. You can confirm the recall by looking at each row in the confusion matrix. For example, if you look at row index 8, you’ll see three 1s and a 2 indicating that some 8s were incorrectly classified as other digits and a 39 indicating that 39 images were correctly classified. So the _recall_ for the digit 8 is 39/44 or 0.89.

- **f1-score**—This is the average of the _precision_ and the _recall_.

- **support**—The number of samples with a given expected value. For example, 50 samples were labeled as 4s, and 38 samples were labeled as 5s.

For details on the averages displayed at the bottom of the report, see:

http://scikit-learn.org/stable/modules/generated/sklearn.metrics.classification_report.html

## Visualizing the Confusion Matrix

A **heat map** displays values as colors, often with values of higher magnitude displayed as more intense colors. Seaborn's graphing functions work with two-dimensional data. When using a pandas `DataFrame` as the data source, Seaborn automatically labels its visualizations using the column names and row indices. Let's convert the confusion matrix into a `DataFrame`, then graph it:

Click here to view code image

```
In [32]: import pandas as pd

In [33]: confusion_df = pd.DataFrame(confusion,   index=range(10),
     ...:                  columns=range(10))
     ...:

In [34]: import seaborn as sns

In [35]: axes = sns.heatmap(confusion_df, annot=True,
     ...:              cmap='nipy_spectral_r')
     ...:
```

The Seaborn function `heatmap` creates a heat map from the specified `DataFrame`. The keyword argument `annot=True` (short for “annotation”) displays a color bar to the right of the diagram, showing how the values correspond to the heat map’s colors. The `cmap='nipy_spectral_r'` keyword argument specifies which color map to use. We used the `nipy_spectral_r` color map with the colors shown in the heat map’s color bar. When you display a confusion matrix as a heat map, the principal diagonal and the incorrect predictions stand out nicely.

![](img/34b7fc2f1ee27beb73bca14927d42340_615_0.png)

## 14.3.2 K-Fold Cross-Validation

**K-fold cross-validation** enables you to use all of your data for _both_ training _and_ testing, to get a better sense of how well your model will make predictions for new data by repeatedly training and testing the model with different portions of the dataset. K-fold cross-validation splits the dataset into _k_ equal-size **folds** (this _k_ is unrelated to _k_ in the k-nearest neighbors algorithm). You then repeatedly train your model with _k_ − 1 folds and test the model with the remaining fold. For example, consider using _k_ = 10 with folds numbered 1 through 10. With 10 folds, we'd do 10 successive training and testing cycles:

- First, we'd train with folds 1–9, then test with fold 10.
- Next, we'd train with folds 1–8 and 10, then test with fold 9.
- Next, we'd train with folds 1–7 and 9–10, then test with fold 8.

This training and testing cycle continues until each fold has been used to test the model.

## KFold Class

Scikit-learn provides the **KFold** class and the `cross_val_score` function (both in the module `sklearn.model_selection`) to help you perform the training and testing cycles described above. Let's perform k-fold cross-validation with the Digits dataset and the `KNeighborsClassifier` created earlier. First, create a `KFold` object:

Click here to view code image

```
In [36]: from sklearn.model_selection import KFold

In [37]: kfold = KFold(n_splits=10, random_state=11, shuffle=True)
```

The keyword arguments are:

- `n_splits=10`, which specifies the number of folds.
- `random_state=11`, which seeds the random number generator for reproducibility.
- `shuffle=True`, which causes the `KFold` object to randomize the data by shuffling it before splitting it into folds. This is particularly important if the samples might be ordered or grouped. For example, the Iris dataset we'll use later in this chapter has 150 samples of three Iris species—the first 50 are Iris setosa, the next 50 are Iris versicolor and the last 50 are Iris virginica. If we do not shuffle the samples, then the training data might contain none of a particular Iris species and the test data might be all of one species.

## Using the KFold Object with Function cross_val_score

Next, use function `cross_val_score` to train and test your model:

Click here to view code image

```
In [38]: from sklearn.model_selection import cross_val_score

In [39]: scores = cross_val_score(estimator=knn, X=digits.data,
   ...: y=digits.target, cv=kfold)
   ...:
```

The keyword arguments are:

- `estimator=knn`, which specifies the estimator you’d like to validate.
- `X=digits.data`, which specifies the samples to use for training and testing.
- `y=digits.target`, which specifies the target predictions for the samples.
- `cv=kfold`, which specifies the cross-validation generator that defines how to split the samples and targets for training and testing.

Function `cross_val_score` returns an array of accuracy scores—one for each fold. As you can see below, the model was quite accurate. Its *lowest* accuracy score was `0.97777778` (97.78%) and in one case it was 100% accurate in predicting an entire fold:

Click here to view code image

```
In [40]: scores
Out[40]:
array([0.97777778, 0.99444444, 0.98888889, 0.97777778, 0.98888889,
       0.99444444, 0.97777778, 0.98882682, 1.        , 0.98324022])
```

Once you have the accuracy scores, you can get an overall sense of the model’s accuracy by calculating the mean accuracy score and the standard deviation among the 10 accuracy scores (or whatever number of folds you choose):

Click here to view code image

```
In [41]: print(f'Mean accuracy: {scores.mean():.2%}')
Mean accuracy: 98.72%
In [42]: print(f'Accuracy standard deviation: {scores.std():.2%}')
Accuracy standard deviation: 0.75%
```

On average, the model was 98.72% accurate—even better than the 97.78% we achieved when we trained the model with 75% of the data and tested the model with 25% earlier.

## 14.3.3 Running Multiple Models to Find the Best One

It’s difficult to know in advance which machine learning model(s) will perform best for a given dataset, especially when they hide the details of how they operate from their users. Even though the KNeighborsClassifier predicts digit images with a high
