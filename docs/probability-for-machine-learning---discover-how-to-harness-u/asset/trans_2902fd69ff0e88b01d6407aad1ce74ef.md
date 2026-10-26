
预测是使用每个训练好的模型进行的。例如，下面是一个展示 API 用法的代码片段：

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

清单 28.3: 使用交叉验证校准概率的 API 示例。

`CalibratedClassifierCV` 类支持两种类型的概率校准；具体来说，可通过 `method` 参数指定的参数化 ‘sigmoid’ 方法（Platt’s method）和非参数化 ‘isotonic’ 方法。

## 28.5 校准 SVM 概率的工作示例

我们可以通过一些实际示例使校准的讨论更具体。在这些示例中，我们将对一个噪声二分类问题拟合支持向量机（SVM），并使用该模型预测概率，然后使用可靠性图检查校准情况并校准分类器并查看结果。SVM 是一个很好的校准候选模型，因为它本身并不原生预测概率，这意味着概率通常未校准。

**关于 SVM 的说明：** 可以通过在拟合模型上调用 `decision_function()` 函数而不是通常的 `predict_proba()` 函数来预测概率。概率未归一化，但在调用 `calibration_curve()` 函数时通过将 `normalize` 参数设置为 `True` 可以进行归一化。下面示例在测试问题上拟合 SVM 模型，预测概率，并将概率的校准情况绘制为可靠性图，

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

清单 28.4: 绘制预测概率可靠性图的示例。

运行该示例会创建可靠性图，显示 SVM 预测概率的校准情况（实线）与沿着绘图对角线的完美校准模型（虚线）相比。我们可以看到保守预测的预期 S 形曲线。

![](img/6ef657cfead7281442f755181c4f6e50_290_0.png)

图 28.1: 未校准 SVM 可靠性图的绘图。

我们可以更新示例，使用 CalibratedClassifierCV 类通过 5 折交叉验证拟合 SVM，使用保留集来校准预测概率。完整示例如下所示。

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

清单 28.5: 绘制校准后概率可靠性图的示例。

运行该示例会创建校准后概率的可靠性图。校准后概率的形状不同，更紧密地贴合对角线，尽管在上象限仍存在低估。视觉上，该图表明模型校准更好。

![](img/6ef657cfead7281442f755181c4f6e50_291_0.png)

图 28.2: 校准后 SVM 可靠性图的绘图。

我们可以通过在同一绘图上包含两个可靠性图，使两种模型之间的对比更明显。完整示例如下所示。

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

清单 28.6: 绘制未校准和校准后概率可靠性图的示例。

运行该示例会创建单个可靠性图，同时显示校准后（橙色）和未校准（蓝色）概率。这并不是真正意义上的苹果对苹果比较，因为校准模型做出的预测实际上是五个子模型的组合。尽管如此，我们确实看到了校准后概率可靠性方面的明显差异（很可能是校准过程造成的）。

![](img/6ef657cfead7281442f755181c4f6e50_293_0.png)

图 28.3: 校准后和未校准 SVM 可靠性图的绘图。

## 28.6 进一步阅读

本节提供了更多资源，如果您想深入了解该主题。

### 28.6.1 书籍和论文

- *应用预测建模*, 2013.
  https://amzn.to/2kXE35G
- *使用监督学习预测良好概率*, 2005.
  https://www.cs.cornell.edu/~alexn/papers/calibration.icml05.crc.rev3.pdf
- *从决策树和朴素贝叶斯分类器中获得校准概率估计*, 2001.
  http://cseweb.ucsd.edu/~elkan/calibrated.pdf
- *提高可靠性图的可靠性*, 2007.
  https://journals.ametsoc.org/doi/abs/10.1175/WAF993.1
