
# List 3.1 IrisClassificationSklearn.ipynb (part 1) with output

```python
import numpy as np
import matplotlib.pyplot as plt

iris_data = np.loadtxt('iris.data',delimiter=',')
x_train = iris_data[0:-1,0:4]
y_train = np.int32(iris_data[0:-1,2:4])
x_test = iris_data[1:,0:4]
y_test = np.int32(iris_data[1:,2:4])
print(x_train.shape)
```

(74, 4)

The next section of code encapsulates a basic machine learning session. In the first step we specify the model, which is here a support vector classifier (SVC) from the SVM methods of sklearn. We then apply a training algorithm in the function that requires both feature values and labels, as this is supervised learning. After the model is trained, we can use the trained model to predict new data. We use the prediction method on the feature values of the test data to predict the correct labels. Finally, we evaluate how good the predictions are by comparing the predicted labels with the test labels. In this case we calculate the percentage of correct labels, which is called the accuracy. The accuracy for this evaluation is around 0.97, which corresponds to only two incorrect classifications.

# List 3.2 IrisClassificationSklearn.ipynb (part 2) with output

```python
from sklearn import svm
# model
model = svm.SVC(kernel='linear')
# train
model.fit(x_train, y_train)
# prediction
y_predicted=model.predict(x_test)
# evaluation
print('Percentage_correct (accuracy) of SVM:', np.mean(y_test == y_predicted))
```

Percentage correct (accuracy) of SVM : 0.972927292972973

Before we move on to discuss evaluations in some detail, let us apply another model, of the popular random forest classifier. The corresponding code is:

# List 3.3 IrisClassificationSklearn.ipynb (part 3) with output

```python
from sklearn.ensemble import RandomForestClassifier
# model
model = RandomForestClassifier(n_estimators=10)
# train
model.fit(x_train, y_train)
# prediction
y_predicted=model.predict(x_test)
# evaluation
print('Percentage_correct (accuracy) of RFC:', np.mean(y_test == y_predicted))
```

Percentage correct (accuracy) of RFC : 0.9459549549549459

The result of this classifier is round 95 percent, equating to four misclassifications. This accuracy is slightly less than the previous results with the SVM classifier, which seems to indicate that the SVM method is superior to RFs. However, this conclusion should not be made as argued further in this chapter. Here, we simply want to show that the framework of applying different models and to show that these results here are similar.

Finally, we show an implementation of a basic neural network called MLP. In the next chapter, we will elaborate on this technique as neural networks have been a major contributor to deep learning have been behind much of the recent machine learning success and will be an important part of our later discussions. The main point here is to show that neural networks can also be framed using the basic model detection, training by fitting the model parameters to the training data and making predictions on test.

# Listing 3.4 IrisClassificationSklearn.ipynb (part 4) with output

```python
from sklearn.neural_network import MLPClassifier
# model
model = MLPClassifier(hidden_layer_sizes=(10, 20, 10))
# train
model.fit(x_train, y_train)
# prediction
y_predicted=model.predict(x_test)
# evaluation
print('%Percentage_correct (accuracy) of MLP:', np.mean(y_test==y_predicted))
```

Percentage correct (accuracy) of MLP : 0.96

Running this code repeatedly will give different values in every run. Most often, these values will be smaller than the ones achieved with SVM and RF, but some are even larger. This demonstrates that more careful consideration of such methods is important.

## 3.2 Performance measures and misclassification and evaluations

We used the performance of misclassification as an objective function to evaluate the performance of the model. This is a common choice and often a good start in our examples, but there are other commonly used evaluation measures that we should understand. Let us consider first binary classification case where it is common to call one "positive" and the other "negative" class. This nomenclature comes from diagnostics such as decide if a person has a disease based on some clinical tests. We then define the following performance indicators,

- True Positive (TP): Number of correctly predicted positive samples

These numbers are summarize in a confusion matrix, and such a matrix layout is shown in Fig. 3.2A.

# Machine learning with sklearn

If we have more than two classes we could generalize this to measures of True Class 1, True Class 2, False Class 1, etc. It is convenient to summarize these numbers in a matrix which lists the true class down the columns and the predicted label along the rows. An example of a confusion matrix for the iris dataset that has three classes is shown in Fig. 3.2B. It is produced with the following code:

# Listing 3.5 Classification/sklearn.ipynb (part 5)

```python
from sklearn import metrics, model_selection
# Confusion Matrix
cm = metrics.confusion_matrix(y_test, y_predicted)
plt.imshow(cm)
plt.yticks('True_label')
plt.ylabel('Predicted_label')
plt.xlabel('Predicted_label')
plt.show()
```

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_48_0)

**Fig. 3.2** Outline of confusion matrix with two classes.

Many measures have been proposed in the literature. For example, if we want to know the ratio (percentage) of correct classification regardless of class, then we can look at the accuracy, $Accuracy = \frac{TP + TN}{TP+FP+FN}$

The denominator is therefore of all data. The true positive rate (TPR) is defined as the number of TP relative to all positive, of which might be false, $True Positive Rate (TPR) = \frac{TP}{TP+FN}$

This measure is also called recall, in computer science arena, or sensitivity, this becomes 100% when simply recalling all samples as positive. It is thus important to balance this with the false positive rate (FPR).

```python
False Positive Rate = \frac{FP}{FP+TN}
```

which we want to make small. This measure is also called out and is the complement to specificity: 1-specificity. In many cases we have the option of trading TPR and FPR by changing some parameters in the algorithm. The resulting trade-off is commonly visualized as an ROC curve. ROC stands for receiver operating characteristics, which comes from their historical use in evaluating communication equipment. Some examples of ROC curves are shown in Fig. 3.3. Ideally, we want the TPR to be one and the FPR to be zero, which corresponds to a point in the upper-left corner. While this is not the case in practice, we want this curve to as close as possible to this point. In other words, we want the area under the curve to be close to 1. In contrast, a random binary classification corresponds to the diagonal curve in this plot, which has a value of 0.5 as the area under this curve. Hence, when comparing two algorithm, we generally prefer an algorithm that has a larger area under the ROC curve, or an area that is close to 1. For many applications we have curves that are somewhere between the two.

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_49_0)

**Fig. 3.3** Example of an ROC curve. The ideal classifier is in the upper-left corner.

While we have already mentioned several measures, there are many more definitions floating around in the literature. For example, the precision is defined as

$$Precision = \frac{TP}{TP+FP}$$

and the recall is defined as

$$Recall = \frac{TP}{TP+FN}$$

A popular way to summarize the precision and recall is to take their harmonic mean

$$F_1 = 2 \cdot \frac{precision \cdot recall}{precision + recall}$$
