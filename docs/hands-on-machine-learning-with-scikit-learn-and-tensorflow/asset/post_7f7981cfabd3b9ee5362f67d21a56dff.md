
```python
from sklearn.metrics import precision_recall_curve
```

precisions, recalls, thresholds = precision_recall_curve(y_train_5, y_scores)
Finally, you can plot precision and recall as functions of the threshold value using
Matplotlib(Figure 3-4):
```python
def plot_precision_recall_vs_threshold(precisions, recalls, thresholds):
    plt.plot(thresholds, precisions[:-1], "b--", label="Precision")
    plt.plot(thresholds, recalls[:-1], "g-", label="Recall")
    [... # highlight the threshold, add the legend, axis label and grid

plot_precision_recall_vs_threshold(precisions, recalls, thresholds)
plt.show()
```

![](img/0684d2da98e09085c0a622d4fd69aaad_122_0.png)

Figure 3-4. Precision and recall versus the decision threshold

You may wonder why the precision curve is bumpier than the recall that precision sometimes goes
down when you raise the threshold (although in general it will go
down). To understand why, look back at Figure 3-3 and notice what
happens when you start from the central threshold and move it just digit to the right: precision goes from 4/5 (80%) down to 3/4
(75%). On the other hand, recall can only go down when the threshold is increased, which explains why its curve looks smooth.

Another way to select a good precision/recall tradeoff is to plot precision directly
against recall, as shown in Figure 3-5 (the same threshold as earlier is highlighted).

![](img/0684d2da98e09085c0a622d4fd69aaad_123_0.png)

Figure 3-5. Precision versus recall

You can see that precision starts to fall sharply around 80% recall. You will probably want to select a precision/recall tradeoff just before that drop—for example, at 60% recall. But of course the choice depends on your project.

So let's suppose you decide to aim for 90% precision. You look up the first plot and find that you need to use a threshold of about 8,000. To be more precise you can search for the lowest threshold that gives you at least 90% precision (np.argmax() will give us the index of the maximum value, in which case means the first True value):

```python
threshold_90_precision = thresholds[np.argmax(precisions >= 0.90)] # -7816
```

To make predictions (on the training set for now), instead of calling the classifier's predict(method), you can run just this code:

```python
>>> precision_score(y_train_5, y_train_pred_90)
0.9006380083618396
>>> recall_score(y_train, y_train_pred_90)
0.43681979492714
```

Let's check these predictions' precision and recall:

Great, you have a 90% precision classifier! As you can see, it is fairly easy to create a classifier with virtually any precision you want: just set a high enough threshold, and you're done. Hmm, not so fast. A high-precision classifier is not very useful if its recall is too low!

# The ROC Curve

The receiver operating characteristic (ROC) curve is another common tool used with binary classifiers. It is very similar to the precision/recall curve, but instead of plotting precision versus recall, the ROC curve plots the true positive rate (another name for recall) against the false positive rate. FPR is the ratio of negative instances that are incorrectly classified as positive. It is equal to one minus the true negative rate, which is the ratio of negative instances that are correctly classified as negative. The TNR is also called specificity. Hence the ROC curve sensitivity (recall) versus 1 – specificity.

To plot the ROC curve, you first need to compute the TPR and FPR for various threshold values, using the roc_curve() function:

```python
from sklearn.metrics import roc_curve

fpr, tpr, thresholds = roc_curve(y_train_5, y_scores)

def plot_roc_curve(fpr, tpr, linewidth=2, label=label):
    plt.plot([0, 1], ['k--']) # dashed diagonal
    [...] # Add axis labels and grid
```

Then you can plot the FPR against the TPR using Matplotlib. This code produces the plot in Figure 3-6:

```python
plt.roc_curve(fpr, tpr)
plt.show()
```

![](img/0684d2da98e09085c0a622d4fd69aaad_125_0.png)

Once again, there is a tradeoff: the higher the recall (TPR), the more false positives (FPR) the classifier produces. The dotted line represents the ROC curve of a purely random classifier; a good classifier stays as far away possible (toward the top-left corner).

One way to compare classifiers is to measure the area under the curve (AUC). A perfect classifier will have a ROC AUC equal to 1, whereas a purely random classifier will have a ROC AUC equal to 0.5. Scikit-Learn provides a function to compute the ROC AUC:

```python
>>> from sklearn.metrics import roc_auc_score
>>> roc_auc_score(y_train_5, y_scores)
0.96117889310184
```

Since the ROC curve is so similar to the precision/recall (or PR) curve, you may wonder how to decide which one to use. As a rule of thumb, you should prefer the PR curve whenever the positive class is rare or when you care more about the false positives than the false negatives, and the ROC curve otherwise. For example, looking at the ROC curve (and ROC AUC score), you may think the classifier is really good. But this is mostly because there are few positives (5s) compared to the negatives (non-5s). In contrast, the PR curve makes it clear that the classifier has room for improvement (the curve could be closer to the top-right corner).

Figure 3-6. ROC curve

Let's train a RandomForestClassifier and compare its ROC curve and ROC AUC score to the SGDClassifier. First, you need to get scores for each instance in the training set. But due to the way it works (see Chapter 7), the RandomForestClassifier does not have a decision_function() method. Instead it has a predict_proba() method. Scikit-learn classifiers generally have one or the other. The predict_proba() method returns an array containing a row per instance and each column containing the probability that the instance belongs to the given class (e.g., 70% chance that the image represents 5):

```python
from sklearn.ensemble import RandomForestClassifier

forest_clf = RandomForestClassifier(random_state=42)
y_probas_forest = cross_val_predict(forest_clf, X_train, y_train_5, cv=3, method='predict_proba')
```

```python
y_scores_forest = y_probas_forest[:, 1] # score = proba of positive class
fpr_forest, tpr_forest, thresholds_forest = roc_curve(y_train_5, y_scores_forest)

plt.plot(fpr_forest, tpr_forest, b="b", label="SGD")
plt.plot(fpr_forest, tpr_forest, "Random Forest")
plt.legend(loc="lower right")
plt.show()
```

Now you are ready to plot the ROC curve. It is useful to plot the first ROC curve as well to see how they compare (Figure 3-7):

![](img/0684d2da98e09085c0a622d4fd69aaad_126_0.png)

Figure 3-7. Comparing ROC curves

As you can see in Figure 3-7, the RandomForestClassifier:s ROC curve looks much better than the SGDClassifier: it comes much closer to the top-left corner. As a result, its ROC AUC score is also significantly better:

```python
>>> roc_auc_score(y_train_5, y_forest)
0.998346371328145
```

Try measuring the precision and recall scores: you should find 99.0% precision and 86.6% recall. Not too bad!

Hopefully you now know how to train binary classifiers, choose the appropriate metric for your task, evaluate your classifiers using cross-validation, select the precision/recall tradeoff that fits your needs, and compare various models using ROC curves and ROC AUC scores. Now let's try to detect more than just the 5s.

# Multiclass Classification

Binary classifiers distinguish between two classes, multiclass classifiers (also multinomial classifiers) can distinguish between more than two classes.

Some algorithms (such as Random Forest classifiers or naive Bayes classifiers) are capable of handling multiple classes. Others (such as Support Vector Machine classifiers or Linear classifiers) are strictly binary classifiers. However, there are strategies that you can use to perform multiclass classification using multiple binary classifiers.

For example, one way to create a system that can classify the digit images into 10 classes (from 0 to 9) is to train 10 binary classifiers, one for each digit (a 0-detector, a 1-detector, a 2-detector, and so on). When you want to classify an image, you get the decision score from each classifier for that image and select the class whose classifier outputs the highest score. This is called the one-versus-all (OvA) strategy (also called one-versus-the-rest).

Another strategy is to train a binary classifier for every pair of digits: one to distinguish 0s and 1s, another for 1s and 2s, and so on. This is called the one-versus-one (OvO) strategy. If there are N classes, you need to train N × (N - 1) / 2 classifiers. For the MNIST dataset, this means training 45 binary classifiers! When you want to classify an image, you have to run the image through all 45 classifiers and see which class wins the duels. The main advantage of OvA is that each classifier only needs to be trained on the part of the training set for the two classes that it distinguish.
