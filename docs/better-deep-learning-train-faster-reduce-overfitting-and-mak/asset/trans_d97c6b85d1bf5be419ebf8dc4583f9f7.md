
模型训练 500 个训练轮次，并在每个轮次结束时对测试数据集进行评估，同时评估训练数据集。

```
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=500, verbose=0)
```

清单 7.14：拟合 MLP 模型的示例。

拟合模型后，它会在训练集和测试集上进行评估，并显示准确率分数。

```
# evaluate the model
_, train_acc = model.evaluate(trainX, trainy, verbose=0)
_, test_acc = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))
```

清单 7.15：评估 MLP 模型的示例。

最后，模型在训练的每个步骤中的准确率被绘制为线图，显示模型学习问题的动态过程。

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

清单 7.16：绘制 MLP 模型学习曲线的示例。

将所有这些结合起来，完整示例列在下面。

```
# mlp with tanh for the two circles classification problem
from sklearn.datasets import make_circles
from sklearn.preprocessing import MinMaxScaler
from keras.layers import Dense
from keras.models import Sequential
from keras.optimizers import SGD
from keras.initializers import RandomUniform
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_circles(n_samples=1000, noise=0.1, random_state=1)
# scale input data to [-1,1]
scaler = MinMaxScaler(feature_range=(-1, 1))
X = scaler.fit_transform(X)
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
init = RandomUniform(minval=0, maxval=1)
model.add(Dense(5, input_dim=2, activation='tanh', kernel_initializer=init))
model.add(Dense(1, activation='sigmoid', kernel_initializer=init))
# compile model
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=500, verbose=0)
# evaluate the model
_, train_acc = model.evaluate(trainX, trainy, verbose=0)
_, test_acc = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))
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

清单 7.17：评估两圆问题中基于 tanh 的 MLP 的示例。

运行示例只需几秒钟即可拟合模型。模型在训练集和测试集上的性能将被计算并显示。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

我们可以看到，在这种情况下，模型很好地学习了问题，在训练集和测试集上均达到了约 81.6% 的准确率。

```
Train: 0.800, Test: 0.820
```

清单 7.18：评估两圆问题中旧式 MLP 的示例输出。

创建了模型在训练集和测试集上的损失和准确率的线图，显示了在全部 500 个训练轮次中性能的变化。图表表明，在本次运行中，性能在大约第 200 个轮次左右开始放缓，训练集和测试集的准确率均约为 80%。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_191_0.png)

图 7.3：两圆问题中 MLP 在训练轮次中训练集和测试集准确率的线图。

现在我们已经看到了如何使用 tanh 激活函数为两圆问题开发经典 MLP，我们可以查看如何修改模型以具有更多隐藏层。

## 7.3.3 更深的 MLP 模型

传统上，开发深度多层感知器模型具有挑战性。使用双曲正切激活函数的深度模型不易训练，而这种较差的性能很大程度上被归咎于梯度消失问题。我们可以尝试使用上一节中开发的 MLP 模型来研究这个问题。隐藏层的数量可以从 1 增加到 5；例如：

```
# define model
init = RandomUniform(minval=0, maxval=1)
model = Sequential()
model.add(Dense(5, input_dim=2, activation='tanh', kernel_initializer=init))
model.add(Dense(5, activation='tanh', kernel_initializer=init))
model.add(Dense(5, activation='tanh', kernel_initializer=init))
model.add(Dense(5, activation='tanh', kernel_initializer=init))
model.add(Dense(5, activation='tanh', kernel_initializer=init))
model.add(Dense(1, activation='sigmoid', kernel_initializer=init))
```

# 清单 7.19：定义更深的基于 tanh 的 MLP 的示例。

然后我们可以重新运行示例并查看结果。更深的 MLP 的完整示例列在下面。

```python
# deeper mlp with tanh for the two circles classification problem
from sklearn.datasets import make_circles
from sklearn.preprocessing import MinMaxScaler
from keras.layers import Dense
from keras.models import Sequential
from keras.optimizers import SGD
from keras.initializers import RandomUniform
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_circles(n_samples=1000, noise=0.1, random_state=1)
scaler = MinMaxScaler(feature_range=(-1, 1))
X = scaler.fit_transform(X)
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
init = RandomUniform(minval=0, maxval=1)
model = Sequential()
model.add(Dense(5, input_dim=2, activation='tanh', kernel_initializer=init))
model.add(Dense(5, activation='tanh', kernel_initializer=init))
model.add(Dense(5, activation='tanh', kernel_initializer=init))
model.add(Dense(5, activation='tanh', kernel_initializer=init))
model.add(Dense(5, activation='tanh', kernel_initializer=init))
model.add(Dense(1, activation='sigmoid', kernel_initializer=init))
# compile model
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=500, verbose=0)
# evaluate the model
_, train_acc = model.evaluate(trainX, trainy, verbose=0)
_, test_acc = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))
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

# 清单 7.20：评估两圆问题中更深的基于 tanh 的 MLP 的示例。

运行示例首先打印拟合模型在训练集和测试集上的性能。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

在这种情况下，我们可以看到性能在训练集和测试集上都很差，准确率约为 50%。这表明按此配置的模型无法学习问题，也无法泛化解决方案。

```
Train: 0.588, Test: 0.552
```

清单 7.21：评估两圆问题中更深的基于 tanh 的 MLP 的示例输出。

模型在训练过程中在训练集和测试集上的准确率线图讲述了类似的故事。我们可以看到性能很差，并且随着训练的进行实际上变得更糟。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_193_0.png)

图 7.4：两圆问题中深度 MLP 在训练轮次中训练集和测试集准确率的线图。

## 7.3.4 使用 ReLU 的更深 MLP 模型

修正线性激活函数已取代双曲正切激活函数，成为开发多层感知器网络以及其他
