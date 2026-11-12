# Confusion matrix

In machine learning, a confusion matrix is also termed as error matrix. The confusion matrix is denoted as a table that is used to define the classification model performance on a set of test data at which we have the known true or correct values.

It also permits the conception of the algorithm performance as it also permits easy recognition of a type of confusion among classes. For example, say one class is mislabeled with respect to the other class. Most of the measures of performance are defined from the confusion matrix.

The confusion matrix is basically a summary of the results of predicted results for a classification-type problem. Here, the number of incorrect and correct predictions is described with a number of count values and then further shattered down by each of the classes.

The confusion matrix depicts the number of ways in which the model for classification is confused while making the predictions. It also gives us a vision that not only the faults being made by a classifier are important, but also the different types of errors that are made are important.

| No. of instances | Class 1 – prediction | Class 2 – prediction |
|------------------|----------------------|----------------------|
| Actual – Class A | FP                   | TN                   |
| Actual – Class B | TP                   | FN                   |

Table 2.9: Confusion matrix syntax

Where TP depicts True Positive

FP depicts False Positive

TN depicts True Negative

FN depicts False Negative

The description of the terms linked with the confusion matrix are as follows:

+   - True Positives (TP): It is the case when both the actual class and predicted class is 1.
+   - True Negatives (TN): It is the case when both the actual class and predicted class is 0.
+   - False Positives (FP): It is the case when the actual class is 0, and the predicted class of data point is 1.