# 82 Mastering Classification Algorithms for Machine Learning

After over-sampling, we see we have the same number of samples for each segment.
Now that the training data is ready, we can build the KNN model and check its goodness during the training phase. For classification, there is KNeighborsClassifier from Scikit-Learn. Notice that KNeighborClassifier is available from sklearn.neighbors package:

```
from sklearn.neighbors import KNeighborsClassifier
```

```
model = KNeighborsClassifier()
model.fit(XO, y0)
```

Notice that we fit the model using the datasets stored in XO and yO, that is, the data obtained over-sampling.
Now that the model is ready, we can make predictions from the model and check the metrics. We got an accuracy of 99.74227% for the training dataset. This can be considered an excellent accuracy score.

Next, we make the predictions on the test dataset and check the accuracy:

```
import matplotlib.pyplot as plt
from sklearn.metrics import ConfusionMatrixDisplay
from sklearn.metrics import accuracy_score
```

```
y_testPred = model.predict(X_test)
availableClasses = list(set(y_testPred)) & set(y_test)
```

```
disp = ConfusionMatrixDisplay.from_predictions(y_test,
y_testPred,
display_labels =
availableClasses)
fig = disp.ax_.get_fig()
fig.set_figheight(10)
fig.set_figwidth(15)
plt.show()
print("\nAccuracy = %.5f%%" % (accuracy_score(y_test, y_testPred) * 100, "%%")"))
```