

```
# generate regression dataset
X, y = make_regression(n_samples=1000, n_features=20, noise=0.1, random_state=1)
```

清单6.6：生成回归问题样本的示例。

每个输入变量都服从高斯分布，目标变量也是如此。我们可以通过绘制部分输入变量和输出变量的直方图来证明这一点。

```
# regression predictive modeling problem
from sklearn.datasets import make_regression
from matplotlib import pyplot
# generate regression dataset
X, y = make_regression(n_samples=1000, n_features=20, noise=0.1, random_state=1)
# histograms of input variables
pyplot.subplot(211)
pyplot.hist(X[:, 0])
pyplot.subplot(212)
pyplot.hist(X[:, 1])
pyplot.show()
# histogram of target variable
pyplot.hist(y)
pyplot.show()
```

清单6.7：生成样本并绘制回归问题分布的示例。

运行该示例会生成两个图。第一个图显示了二十个输入变量中前两个变量的直方图，表明每个变量都服从高斯数据分布。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_161_0.png)

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_161_1.png)

图6.1：回归问题中二十个输入变量中两个变量的直方图。

第二个图显示了目标变量的直方图，表明该变量的取值范围比输入变量大得多，并且同样呈现高斯数据分布。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_162_0.png)

图6.2：回归问题中目标变量的直方图。

既然我们有了一个可以作为研究基础的回归问题，我们就可以开发一个模型来解决它。

## 6.3.2 使用未缩放数据的多层感知机

我们可以为回归问题开发一个多层感知机（MLP）模型。该模型将在原始数据上进行演示，不对输入或输出变量进行任何缩放。我们预期模型性能通常会较差。第一步是将数据划分为训练集和测试集，以便我们能够拟合和评估模型。我们将从该域中生成1,000个样本，并将数据集一分为二，使用500个样本作为训练集和测试集。

```python
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
```

清单6.8：为建模准备数据集的示例。

接下来，我们可以定义MLP模型。模型将期望接收问题中的20个输入变量，即20个输入。将使用一个具有25个节点和修正线性激活函数的隐藏层。输出层有一个节点，对应于单个目标变量，并使用线性激活函数直接预测实数值。

```
# define model
model = Sequential()
model.add(Dense(25, input_dim=20, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(1, activation='linear'))
```

清单6.9：定义MLP模型的示例。

将使用均方误差损失函数来优化模型，并采用随机梯度下降优化算法，其合理的默认配置为学习率0.01和动量0.9。

```
# compile model
model.compile(loss='mean_squared_error', optimizer=SGD(lr=0.01, momentum=0.9))
```

清单6.10：编译MLP模型的示例。

模型将训练100个轮次，测试集将用作验证集，并在每个训练轮次结束时进行评估。训练结束时，计算训练集和测试集上的均方误差，以了解模型对问题的学习效果。

```
# evaluate the model
train_mse = model.evaluate(trainX, trainy, verbose=0)
test_mse = model.evaluate(testX, testy, verbose=0)
```

清单6.11：评估MLP模型的示例。

最后，使用折线图绘制每个训练轮次结束时训练集和测试集上的均方误差学习曲线，以了解模型在学习该问题时的动态变化。

```
# plot loss during training
pyplot.title('Mean Squared Error')
pyplot.plot(history.history['loss'], label='train')
pyplot.plot(history.history['val_loss'], label='test')
pyplot.legend()
pyplot.show()
```

清单6.12：绘制MLP模型学习曲线的示例。

将这些要素组合在一起，完整示例如下。

```
# mlp with unscaled data for the regression problem
from sklearn.datasets import make_regression
from keras.layers import Dense
from keras.models import Sequential
from keras.optimizers import SGD
from matplotlib import pyplot
# generate regression dataset
X, y = make_regression(n_samples=1000, n_features=20, noise=0.1, random_state=1)
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(25, input_dim=20, activation='relu', kernel_initializer='he_uniform'))
```

```
model.add(Dense(1, activation='linear'))
# compile model
model.compile(loss='mean_squared_error', optimizer=SGD(lr=0.01, momentum=0.9))
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=100, verbose=0)
# evaluate the model
train_mse = model.evaluate(trainX, trainy, verbose=0)
test_mse = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_mse, test_mse))
# plot loss during training
pyplot.title('Mean Squared Error')
pyplot.plot(history.history['loss'], label='train')
pyplot.plot(history.history['val_loss'], label='test')
pyplot.legend()
pyplot.show()
```

清单6.13：在未缩放的回归问题上评估MLP模型的示例。

运行该示例会拟合模型并计算训练集和测试集上的均方误差。在这种情况下，模型无法学习该问题，导致预测值为NaN。由于误差非常大，进而导致用于权重更新的误差梯度也很大，模型权重在训练期间发生了爆炸。

```
Train: nan, Test: nan
```

清单6.14：在未缩放的回归问题上评估MLP模型的输出示例。

这表明，至少需要对目标变量进行某种数据缩放。虽然绘制了训练历史的折线图，但由于模型几乎立即产生了NaN均方误差，图上没有任何内容。

## 6.3.3 使用缩放后输出变量的多层感知机

可以更新示例以对目标变量进行缩放。减小目标变量的尺度，反过来也会减小用于更新权重的梯度的大小，从而使模型和训练过程更加稳定。鉴于目标变量服从高斯分布，一种自然的重新缩放方法是对变量进行标准化。这需要估计变量的均值和标准差，并使用这些估计值来执行重新缩放。最佳实践是估计训练数据集的均值和标准差，并使用这些变量来缩放训练集和测试集。这是为了避免模型评估过程中的任何数据泄漏。scikit-learn的转换器期望输入数据是由行和列组成的矩阵，因此目标变量的一维数组在进行转换之前必须重塑为二维数组。

```
# reshape 1d arrays to 2d arrays
trainy = trainy.reshape(len(trainy), 1)
testy = testy.reshape(len(trainy), 1)
```

清单6.15：重塑目标变量的示例。

然后我们可以创建并应用StandardScaler来重新缩放目标变量。

```
# created scaler
scaler = StandardScaler()
# fit scaler on training dataset
```

```
scaler.fit(trainy)
# transform training dataset
trainy = scaler.transform(trainy)
# transform test dataset
testy = scaler.transform(testy)
```

清单6.16：标准化目标变量的示例。

对目标变量进行重新缩放意味着，在评估模型性能和绘制学习曲线时，计算得到的MSE将使用缩放后变量的平方单位，而不是原始尺度的平方单位。这可能会使在领域背景下解释误差变得困难。在实践中，可以先对测试集目标变量和模型预测进行逆变换，然后使用未缩放数据上的均方根误差来评估模型性能，这可能会有帮助。这将作为练习留给读者。下面列出了在回归问题上对MLP的目标变量进行标准化的完整示例。

```
# mlp with scaled outputs on the regression problem
from sklearn.datasets import make_regression
from sklearn.preprocessing import StandardScaler
from keras.layers import Dense
from keras.models import Sequential
from keras.optimizers import SGD
from matplotlib import pyplot
# generate regression dataset
X, y = make_regression(n_samples=1000, n_features=20, noise=0.1, random_state=1)
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# reshape 1d arrays to 2d arrays
trainy = trainy.reshape(len(trainy), 1)
testy = testy.reshape(len(trainy), 1)
# created scaler
scaler = StandardScaler()
# fit scaler on training dataset
scaler.fit(trainy)
# transform training dataset
trainy = scaler.transform(trainy)
# transform test dataset
testy = scaler.transform(testy)
# define model
model = Sequential()
model.add(Dense(25, input_dim=20, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(1, activation='linear'))
# compile model
model.compile(loss='mean_squared_error', optimizer=SGD(lr=0.01, momentum=0.9))
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=100, verbose=0)
# evaluate the model
train_mse = model.evaluate(trainX, trainy, verbose=0)
test_mse = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_mse, test_mse))
# plot loss during training
pyplot.title('Mean Squared Error Loss')
pyplot.plot(history.history['loss'], label='train')
pyplot.plot(history.history['val_loss'], label='test')
pyplot.legend()
pyplot.show()
```

