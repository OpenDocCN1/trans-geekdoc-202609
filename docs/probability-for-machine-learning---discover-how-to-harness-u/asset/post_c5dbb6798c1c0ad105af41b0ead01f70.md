
Predictions are made using each of the trained models. For example, below is a code snippet showing the API usage:

```python
...
# prepare data
trainX, trainy = ...
testX, testy = ...
# define base model
model = ...
# fit and calibrate model on training data
calibrator = CalibratedClassifierCV(model, cv=3)
calibrator.fit(trainX, trainy)
# evaluate the model
yhat = calibrator.predict(testX)
```

Listing 28.3: Example of the API for calibrating probabilities with cross-validation.

The `CalibratedClassifierCV` class supports two types of probability calibration; specifically, the parametric ‘sigmoid’ method (Platt’s method) and the nonparametric ‘isotonic’ method which can be specified via the `method` argument.

## 28.5 Worked Example of Calibrating SVM Probabilities

We can make the discussion of calibration concrete with some worked examples. In these examples, we will fit a support vector machine (SVM) to a noisy binary classification problem and use the model to predict probabilities, then review the calibration using a reliability diagram and calibrate the classifier and review the result. SVM is a good candidate model to calibrate because it does not natively predict probabilities, meaning the probabilities are often uncalibrated.

**A note on SVM:** probabilities can be predicted by calling the `decision_function()` function on the fit model instead of the usual `predict_proba()` function. The probabilities are not normalized, but can be normalized when calling the `calibration_curve()` function by setting the `normalize` argument to `True`. The example below fits an SVM model on the test problem, predicts probabilities, and plots the calibration of the probabilities as a reliability diagram,

```python
# SVM reliability diagram
from sklearn.datasets import make_classification
from sklearn.svm import SVC
from sklearn.model_selection import train_test_split
from sklearn.calibration import calibration_curve
from matplotlib import pyplot
# generate 2 class dataset
X, y = make_classification(n_samples=1000, n_classes=2, weights=[1,1], random_state=1)
# split into train/test sets
trainX, testX, trainy, testy = train_test_split(X, y, test_size=0.5, random_state=2)
# fit a model
model = SVC(gamma='scale')
model.fit(trainX, trainy)
# predict probabilities
probs = model.decision_function(testX)
# reliability diagram
fop, mpv = calibration_curve(testy, probs, n_bins=10, normalize=True)
# plot perfectly calibrated
pyplot.plot([0, 1], [0, 1], linestyle='--')
# plot model reliability
pyplot.plot(mpv, fop, marker='.')
pyplot.show()
```

Listing 28.4: Example of plotting a reliability diagram for predicted probabilities.

Running the example creates a reliability diagram showing the calibration of the SVM's predicted probabilities (solid line) compared to a perfectly calibrated model along the diagonal of the plot (dashed line). We can see the expected S-shaped curve of a conservative forecast.

![](img/6ef657cfead7281442f755181c4f6e50_290_0.png)

Figure 28.1: Plot of the Uncalibrated SVM Reliability Diagram.

We can update the example to fit the SVM via the CalibratedClassifierCV class using 5-fold cross-validation, using the holdout sets to calibrate the predicted probabilities. The complete example is listed below.

```python
# SVM reliability diagram with calibration
from sklearn.datasets import make_classification
from sklearn.svm import SVC
from sklearn.calibration import CalibratedClassifierCV
from sklearn.model_selection import train_test_split
from sklearn.calibration import calibration_curve
from matplotlib import pyplot
# generate 2 class dataset
X, y = make_classification(n_samples=1000, n_classes=2, weights=[1,1], random_state=1)
# split into train/test sets
trainX, testX, trainy, testy = train_test_split(X, y, test_size=0.5, random_state=2)
# fit a model
model = SVC(gamma='scale')
calibrated = CalibratedClassifierCV(model, method='sigmoid', cv=5)
calibrated.fit(trainX, trainy)
# predict probabilities
probs = calibrated.predict_proba(testX)[:, 1]
# reliability diagram
fop, mpv = calibration_curve(testy, probs, n_bins=10, normalize=True)
# plot perfectly calibrated
pyplot.plot([0, 1], [0, 1], linestyle='--')
# plot calibrated reliability
pyplot.plot(mpv, fop, marker='.')
pyplot.show()
```

Listing 28.5: Example of plotting a reliability diagram for the calibrated probabilities.

Running the example creates a reliability diagram for the calibrated probabilities. The shape of the calibrated probabilities is different, hugging the diagonal line much better, although still under-forecasting in the upper quadrant. Visually, the plot suggests a better calibrated model.

![](img/6ef657cfead7281442f755181c4f6e50_291_0.png)

Figure 28.2: Plot of the Calibrated SVM Reliability Diagram.

We can make the contrast between the two models more obvious by including both reliability diagrams on the same plot. The complete example is listed below.

```python
# SVM reliability diagrams with uncalibrated and calibrated probabilities
from sklearn.datasets import make_classification
from sklearn.svm import SVC
from sklearn.calibration import CalibratedClassifierCV
from sklearn.model_selection import train_test_split
from sklearn.calibration import calibration_curve
from matplotlib import pyplot

# predict uncalibrated probabilities
def uncalibrated(trainX, testX, trainy):
    # fit a model
    model = SVC(gamma='scale')
    model.fit(trainX, trainy)
    # predict probabilities
    return model.decision_function(testX)

# predict calibrated probabilities
def calibrated(trainX, testX, trainy):
    # define model
    model = SVC(gamma='scale')
    # define and fit calibration model
    calibrated = CalibratedClassifierCV(model, method='sigmoid', cv=5)
    calibrated.fit(trainX, trainy)
    # predict probabilities
    return calibrated.predict_proba(testX)[:, 1]

# generate 2 class dataset
X, y = make_classification(n_samples=1000, n_classes=2, weights=[1,1], random_state=1)
# split into train/test sets
trainX, testX, trainy, testy = train_test_split(X, y, test_size=0.5, random_state=2)
# uncalibrated predictions
yhat_uncalibrated = uncalibrated(trainX, testX, trainy)
# calibrated predictions
yhat_calibrated = calibrated(trainX, testX, trainy)
# reliability diagrams
fop_uncalibrated, mpv_uncalibrated = calibration_curve(testy, yhat_uncalibrated, n_bins=10, normalize=True)
fop_calibrated, mpv_calibrated = calibration_curve(testy, yhat_calibrated, n_bins=10)
# plot perfectly calibrated
pyplot.plot([0, 1], [0, 1], linestyle='--', color='black')
# plot model reliabilities
pyplot.plot(mpv_uncalibrated, fop_uncalibrated, marker='.')
pyplot.plot(mpv_calibrated, fop_calibrated, marker='.')
pyplot.show()
```

Listing 28.6: Example of plotting a reliability diagram for the uncalibrated and calibrated probabilities.

Running the example creates a single reliability diagram showing both the calibrated (orange) and uncalibrated (blue) probabilities. It is not really an apples-to-apples comparison as the predictions made by the calibrated model are in fact a combination of five submodels. Nevertheless, we do see a marked difference in the reliability of the calibrated probabilities (very likely caused by the calibration process).

![](img/6ef657cfead7281442f755181c4f6e50_293_0.png)

Figure 28.3: Plot of the Calibrated and Uncalibrated SVM Reliability Diagram.

## 28.6 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 28.6.1 Books and Papers

- *Applied Predictive Modeling*, 2013.
  https://amzn.to/2kXE35G
- *Predicting Good Probabilities With Supervised Learning*, 2005.
  https://www.cs.cornell.edu/~alexn/papers/calibration.icml05.crc.rev3.pdf
- *Obtaining Calibrated Probability Estimates From Decision Trees And Naive Bayesian Classifiers*, 2001.
  http://cseweb.ucsd.edu/~elkan/calibrated.pdf
- *Increasing the Reliability of Reliability Diagrams*, 2007.
  https://journals.ametsoc.org/doi/abs/10.1175/WAF993.1
