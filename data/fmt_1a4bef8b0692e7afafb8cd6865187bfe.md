
也可以改用提前停止。可以多次重复提前停止过程。可以记录训练停止时的 `epoch` 编号。然后，可以在拟合所有可用训练数据的最终模型时使用所有提前停止重复中 `epoch` 编号的平均值。此过程可以在每次运行提前停止时使用训练集的不同划分到训练和验证步骤。另一种替代方法是使用验证数据集进行提前停止，然后在保留的验证集上对最终模型进行进一步训练。

## 提前停止与交叉验证

提前停止可以与 `k` 折交叉验证一起使用，尽管不推荐这样做。`k` 折交叉验证程序旨在通过在数据集的不同子集上反复重新拟合和评估模型来估计模型的泛化误差。提前停止旨在监控单个模型的泛化误差，并在泛化误差开始恶化时停止训练。它们存在矛盾，因为交叉验证假设你不知道泛化误差，而提前停止正试图基于对泛化误差的了解给出最佳模型。

可能希望使用交叉验证来估计具有不同超参数值（例如学习率或网络结构）的模型的性能，同时也使用提前停止。在这种情况下，如果你有资源反复评估模型的性能，那么训练 `epoch` 数也可以被视为需要优化的超参数，而不是使用提前停止。不要使用交叉验证与提前停止，可以直接使用提前停止而无需重复评估来评估模型的不同的超参数值（例如不同的学习率）。一个可能的混淆点是，提前停止有时被称为交叉验证训练。此外，研究提前停止以比较触发条件的论文可能会使用交叉验证来比较不同触发条件的影响。

## 验证集过拟合

多次重复提前停止过程可能会导致模型过拟合验证数据集。这与过拟合训练数据集一样容易发生。一种方法是仅在所有其他模型超参数都已

```
...
model.fit(train_x, train_y, validation_split=0.3)
```

代码18.5：示例：将验证数据集指定为训练集百分比的示例。

在这两种情况下，模型都不会在验证数据集上进行训练。相反，在每个训练轮次结束时，模型会在验证数据集上进行评估。

### 18.2.3 监控模型性能

为模型选择优化的损失函数会在每个轮次结束时计算。对于回调函数来说，该值通过名称 `loss` 提供。如果通过 `fit()` 函数的 `validation_data` 或 `validation_split` 参数指定了验证数据集，那么验证数据集上的损失将通过名称 `val_loss` 提供。在模型训练期间，还可以监控其他指标。这些指标可以在编译模型时通过 `compile` 函数的 `metrics` 参数来指定。该参数接受一个已知度量函数的 Python 列表，例如 `mse` 表示均方误差，`acc` 表示准确率。例如：

```
...
model.compile(..., metrics=['acc'])
```

代码18.6：示例：在训练期间监控准确率。

如果在训练期间监控了其他指标，这些指标也会通过相同名称提供给回调函数，例如 `acc` 表示训练数据集上的准确率，`val_acc` 表示验证数据集上的准确率。或者，`mse` 表示训练数据集上的均方误差，`val_mse` 表示验证数据集上的均方误差。

### 18.2.4 早停回调

Keras 通过名为 `EarlyStopping` 的回调支持提前停止训练。该回调允许你指定要监控的性能指标、触发条件，一旦触发，它将停止训练过程。`EarlyStopping` 回调在实例化时通过参数进行配置。`monitor` 参数允许你指定要监控的性能指标，以便结束训练。回顾上一节，在验证数据集上计算的度量值会带有 `val_` 前缀，例如 `val_loss` 表示验证数据集上的损失。

```
es = EarlyStopping(monitor='val_loss')
```

代码18.7：示例：使用早停监控验证损失。

根据所选的性能指标，`mode` 参数需要指定为所选指标的目标是增加（`maximize` 或 `max`）还是减少（`minimize` 或 `min`）。例如，我们希望验证损失和验证均方误差最小化，而验证准确率则希望最大化。

```
es = EarlyStopping(monitor='val_loss', mode='min')
```

代码18.8：示例：使用早停监控最小化验证损失。

默认情况下，`mode` 设置为 `auto`，它会自动知道你想要最小化损失或最大化准确率。这就是最简单形式的早停所需的全部设置。当所选的性能指标停止改善时，训练将停止。要发现训练停止时的训练轮次，可以将 `verbose` 参数设置为 `1`。一旦停止，回调将打印轮次数。

```
es = EarlyStopping(monitor='val_loss', mode='min', verbose=1)
```

代码18.9：示例：带详细输出的早停。

通常，首次出现无进一步改善的迹象可能不是停止训练的最佳时机。这是因为模型可能会进入一个无改善的平台期，甚至在变得更好之前会稍微变差。我们可以通过添加一个延迟触发来考虑这一点，即在多少个轮次内我们希望看不到改善。这可以通过设置 `patience` 参数来实现。

```
es = EarlyStopping(monitor='val_loss', mode='min', verbose=1, patience=50)
```

代码18.10：示例：带耐心值的早停。

确切的耐心值会因模型和问题而异。查看性能指标的图表对于了解模型在你的数据上的优化过程可能有多大的噪声非常有帮助。默认情况下，性能指标的任何变化，无论多微小，都被视为改善。你可能希望将改善视为一个特定的增量，例如均方误差的 `1` 个单位或准确率的 `1%`。这可以通过 `min_delta` 参数来指定。

```
es = EarlyStopping(monitor='val_acc', mode='max', min_delta=1)
```

代码18.11：示例：带最小增量的早停。

最后，可能希望只在性能保持在给定阈值或基线上方或下方时才停止训练。例如，如果你熟悉模型的训练过程（如学习曲线），并且知道一旦达到某个给定的验证损失值，继续训练就没有意义了。这可以通过设置 `baseline` 参数来指定。这在微调模型时可能更有用，此时模型训练早期阶段性能指标中的初始大幅波动已经过去。

```
es = EarlyStopping(monitor='val_loss', mode='min', baseline=0.4)
```

代码18.12：示例：带基线的早停。

### 18.2.5 模型检查点

`EarlyStopping` 回调一旦触发就会停止训练，但训练结束时的模型可能不是在验证数据集上表现最佳的模型。需要另一个回调来保存训练期间观察到的最佳模型以供后续使用。这就是 `ModelCheckpoint` 回调。`ModelCheckpoint` 回调的使用方式非常灵活，但在本例中，我们只使用它来保存训练期间观察到的最佳模型，该模型由验证数据集上的所选性能指标定义。保存和加载模型要求你的工作站上已安装 HDF5 支持。例如，使用 `pip` Python 安装程序，可以通过以下方式实现：

```
sudo pip install h5py
```

代码18.13：通过 pip 安装 h5py 库。

你可以从 `h5py` 安装文档¹ 中了解更多信息。该回调会将模型保存到文件，这需要通过第一个参数指定路径和文件名。

```
mc = ModelCheckpoint('best_model.h5')
```

代码18.14：示例：创建模型检查点回调。

可以通过 `monitor` 参数指定要监控的首选损失函数，方式与 `EarlyStopping` 回调相同。例如，验证数据集上的损失（默认值）。

```
mc = ModelCheckpoint('best_model.h5', monitor='val_loss')
```

代码18.15：示例：监控验证损失的模型检查点。

另外，与 `EarlyStopping` 回调一样，我们必须将 `mode` 指定为最小化或最大化性能指标。同样，默认值是 `auto`，它能够识别标准性能指标。

```
mc = ModelCheckpoint('best_model.h5', monitor='val_loss', mode='min')
```

代码18.16：示例：监控最小化验证损失的模型检查点。

最后，我们只对训练期间观察到的“最佳”模型感兴趣，而不是相对于上一个轮次的最佳模型，因为如果训练有噪声，上一个轮次的最佳模型可能不是总体最佳模型。这可以通过将 `save_best_only` 参数设置为 `True` 来实现。

```
mc = ModelCheckpoint('best_model.h5', monitor='val_loss', mode='min', save_best_only=True)
```

代码18.17：示例：仅保存最佳模型的模型检查点。

这就是在使用早停时或一般情况下确保保存最佳性能模型所需的全部设置。了解性能指标的值以及模型被保存的轮次可能会很有趣。这可以通过将 `verbose` 参数设置为 `1` 来由回调打印出来。

```
mc = ModelCheckpoint('best_model.h5', monitor='val_loss', mode='min', verbose=1)
```

代码18.18：示例：带详细输出的模型检查点。

之后，可以随时通过调用 `load_model()` 函数来加载并评估保存的模型。

```
# 加载保存的模型
from keras.models import load_model
saved_model = load_model('best_model.h5')
```

代码18.19：示例：加载检查点模型。

现在我们知道了如何使用早停和模型检查点 API，接下来看一个实际示例。

## 18.3 早停案例研究

在本节中，我们将演示如何在一个简单的二分类问题上使用早停来减少 MLP 的过拟合。此示例为将早停应用于你自己的分类和回归问题的神经网络提供了一个模板。

### 18.3.1 二分类问题

我们将使用一个标准的二分类问题，该问题定义了两个半圆形的观测数据，每个类别一个半圆。每个观测数据有两个尺度相同的输入变量，以及一个类别输出值，取值为0或1。由于绘制时每个类别中观测数据的形状，这个数据集被称为“moons”数据集。我们可以使用 `make_moons()` 函数生成该问题的观测数据。我们将向数据中添加噪声，并设定随机数生成器的种子，以保证每次运行代码时生成相同的样本。

```
# generate 2d classification dataset
X, y = make_moons(n_samples=100, noise=0.2, random_state=1)
```

清单 18.20：创建两个月亮问题样本的示例。

我们可以绘制数据集，其中两个变量分别作为图上的x和y坐标，类别值作为观测数据的颜色。下面给出了生成数据集并绘制它们的完整示例。

```
# scatter plot of moons dataset
from sklearn.datasets import make_moons
from matplotlib import pyplot
from numpy import where
# generate 2d classification dataset
X, y = make_moons(n_samples=100, noise=0.2, random_state=1)
# scatter plot for each class value
for class_value in range(2):
    # select indices of points with the class label
    row_ix = where(y == class_value)
    # scatter plot for points with a different color
    pyplot.scatter(X[row_ix, 0], X[row_ix, 1])
# show plot
pyplot.show()
```

清单 18.21：绘制两个月亮问题样本的示例。

运行该示例会生成一个散点图，显示每个类别中观测数据的半圆或月亮形状。我们可以看到点分布中的噪声使得月亮的形状不那么明显。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_389_0.png)

图18.1：月亮数据集的散点图，其中颜色显示了每个样本的类别值。

这是一个很好的测试问题，因为类别无法用直线分开，即不是线性可分的，需要诸如神经网络之类的非线性方法来解决。我们只生成了100个样本，这对神经网络来说规模较小，提供了过拟合训练数据集的机会，并导致测试数据集上误差更高：这是使用正则化的一个好场景。此外，样本中带有噪声，使得模型有机会学习样本中无法泛化的方面。

### 18.3.2 过拟合多层感知机

我们可以开发一个MLP模型来解决这个二分类问题。该模型将包含一个隐藏层，其节点数超过解决该问题所需的数量，从而提供过拟合的机会。我们还会对模型进行超出必要时长的训练，以确保模型过拟合。在定义模型之前，我们将数据集划分为训练集和测试集，使用30个样本训练模型，70个样本评估拟合模型的性能。

```
# generate 2d classification dataset
X, y = make_moons(n_samples=100, noise=0.2, random_state=1)
# split into train and test
n_train = 30
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
```

清单 18.22：创建可用于建模的数据集的示例。

接下来，我们可以定义模型。隐藏层使用500个节点和修正线性激活函数。输出层使用sigmoid激活函数来预测0或1的类别值。模型使用二元交叉熵损失函数进行优化，该函数适用于二分类问题，并采用高效的Adam梯度下降版本。

```
# define model
model = Sequential()
model.add(Dense(500, input_dim=2, activation='relu'))
model.add(Dense(1, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
```

清单 18.23：定义MLP模型的示例。

然后，所定义的模型在训练数据上拟合4,000个轮次（epochs），默认批量大小为32。我们还将测试数据集用作验证数据集。这只是本示例的简化处理。在实践中，你应该将训练集划分为训练集和验证集，并留出一个测试集用于最终模型评估。

```
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=4000, verbose=0)
```

清单 18.24：拟合MLP模型的示例。

我们可以评估模型在测试数据集上的性能，并报告结果。

```
# evaluate the model
_, train_acc = model.evaluate(trainX, trainy, verbose=0)
_, test_acc = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))
```

清单 18.25：评估MLP模型的示例。

最后，我们将绘制模型在每个轮次中训练集和测试集上的损失与准确率。如果模型确实过拟合了训练数据集，我们预计训练集上的损失（和准确率）折线图会持续上升，而测试集则先上升后下降，因为模型学习了训练数据中的统计噪声。

```
# plot loss learning curves
pyplot.subplot(211)
pyplot.title('Cross-Entropy Loss', pad=-40)
pyplot.plot(history.history['loss'], label='train')
pyplot.plot(history.history['val_loss'], label='test')
pyplot.legend()
# plot accuracy learning curves
pyplot.subplot(212)
pyplot.title('Accuracy', pad=-40)
pyplot.plot(history.history['acc'], label='train')
pyplot.plot(history.history['val_acc'], label='test')
pyplot.legend()
pyplot.show()
```

清单 18.26：绘制MLP模型学习曲线的示例。

我们可以把所有片段组合在一起；完整示例如下所示。
