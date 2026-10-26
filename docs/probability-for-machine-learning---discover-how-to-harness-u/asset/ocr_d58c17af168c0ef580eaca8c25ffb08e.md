+   - **Insensitivity to Class Imbalance.** ROC AUC is a summary on the models ability to correctly discriminate a single example across different thresholds. As such, it is unconcerned with the base likelihood of each class.

Below, the example demonstrating the ROC curve is updated to calculate and display the AUC.

```
```python
# roc auc
from sklearn.datasets import make_classification
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import roc_auc_score
# generate 2 class dataset
X, y = make_classification(n_samples=1000, n_classes=2, random_state=1)
# split into train/test sets
trainX, testX, trainy, testy = train_test_split(X, y, test_size=0.5, random_state=2)
# fit a model
model = LogisticRegression(solver='lbfgs')
model.fit(trainX, trainy)
# predict probabilities
probs = model.predict_proba(testX)
# keep probabilities for the positive outcome only
probs = probs[:, 1]
# calculate roc auc
auc = roc_auc_score(testy, probs)
print(auc)
```
```

Listing 26.8: Example of calculating the ROC AUC for predictions.

Running the example calculates and prints the ROC AUC for the logistic regression model evaluated on 500 new examples.

```
```text
0.9028205128205128
```
```

Listing 26.9: Example output from calculating the ROC AUC for predictions.

An important consideration in choosing the ROC AUC is that it does not summarize the specific discriminative power of the model, rather the general discriminative power across all thresholds. It might be a better tool for model selection rather than in quantifying the practical skill of a model’s predicted probabilities.

# 26.5 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

# 26.5.1 API

+   - sklearn.metrics.log_loss API.  
+     http://scikit-learn.org/stable/modules/generated/sklearn.metrics.log_loss.html
+   - sklearn.metrics.brier_score_loss API.  
+     http://scikit-learn.org/stable/modules/generated/sklearn.metrics.brier_score_loss.html