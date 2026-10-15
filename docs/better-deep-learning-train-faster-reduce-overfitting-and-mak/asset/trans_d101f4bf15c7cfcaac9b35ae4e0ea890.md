
![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_366_0.png)

图 17.1：散点图显示圆环数据集，颜色表示每个样本的类别值。

这是一个很好的测试问题，因为类别无法通过一条直线分离，例如不是线性可分的，需要使用神经网络等非线性方法来解决。我们仅生成了 100 个样本，对于神经网络来说数量很少，这提供了过度拟合训练数据集并在测试数据集上产生更高误差的机会，是使用正则化的一个良好案例。此外，样本具有噪声，给模型提供了学习样本中不具泛化性的方面的机会。

### 17.3.2 过拟合多层感知器

我们可以开发一个 MLP 模型来解决此二分类问题。该模型将有一个隐藏层，其节点数多于解决此问题可能所需的节点数，从而提供过度拟合的机会。我们还将比所需时间更长地训练模型，以确保模型过拟合。在定义模型之前，我们将把数据集划分为训练集和测试集，使用 30 个示例来训练模型，70 个示例来评估拟合模型的性能。

```
# generate 2d classification dataset
X, y = make_circles(n_samples=100, noise=0.1, random_state=1)
# split into train and test
n_train = 30
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
```

### 列表 17.10：准备数据集用于建模的示例。

接下来，我们可以定义模型。隐藏层使用 500 个节点和整流线性激活函数。输出层使用 sigmoid 激活函数以预测 0 或 1 的类别值。模型使用二元交叉熵损失函数进行优化，该函数适用于二分类问题以及高效的 Adam 梯度下降版本。

```
# define model
model = Sequential()
model.add(Dense(500, input_dim=2, activation='relu'))
model.add(Dense(1, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
```

### 列表 17.11：定义 MLP 模型的示例。

然后将定义的模型在训练数据上拟合 4,000 个 epoch，默认批大小为 32。我们还将使用测试数据集作为验证数据集。

```
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=4000, verbose=0)
```

### 列表 17.12：拟合 MLP 模型的示例。

我们可以评估模型在测试数据集上的性能并报告结果。

```
# evaluate the model
_, train_acc = model.evaluate(trainX, trainy, verbose=0)
_, test_acc = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))
```

### 列表 17.13：评估 MLP 模型的示例。

最后，我们将绘制模型在每个 epoch 上在训练集和测试集上的性能。如果模型确实对训练数据集过拟合，我们期望训练集上的准确率线图持续上升，而测试集则先上升后再次下降，因为模型学习了训练数据集中的统计噪声。

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

### 列表 17.14：绘制拟合 MLP 模型学习曲线的示例。

我们可以将所有这些部分结合起来；完整示例列在下面。

```
# mlp overfit on the two circles dataset
from sklearn.datasets import make_circles
from keras.layers import Dense
from keras.models import Sequential
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_circles(n_samples=100, noise=0.1, random_state=1)
# split into train and test
n_train = 30
trainX, testX = X[: n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(500, input_dim=2, activation='relu'))
model.add(Dense(1, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=4000, verbose=0)
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

列表 17.15：两圆问题上 MLP 拟合的示例。

运行示例报告模型在训练集和测试数据集上的性能。我们可以看到模型在训练数据集上的性能优于测试数据集，这是过拟合的可能迹象之一。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

```
Train: 1.000, Test: 0.771
```

列表 17.16：在两圆问题上拟合 MLP 的示例输出。

创建了一个图形，显示模型在训练集和测试集上的准确率线图。我们可以看到过拟合模型的预期形状，其中测试准确率增加到某一点然后开始再次下降。

## 17.3. 噪声正则化案例研究

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_369_0.png)

图 17.2：训练过程中训练集和测试数据集准确率的线图显示过拟合。

数据集由具有受控统计噪声量的点定义。尽管如此，由于数据集很小，我们可能希望对输入值添加更多噪声。这将产生创建更多样本或重新采样域的效果，使输入空间的结构人为地更平滑。这可能使问题更容易学习并提高泛化性能。我们可以将 GaussianNoise 层添加为输入层。噪声量必须很小。鉴于输入值在 [0, 1] 范围内，我们将添加均值为 0.0、标准差为 0.01 的高斯噪声，该值是任意选择的。

```
# define model
model = Sequential()
model.add(GaussianNoise(0.01, input_shape=(2,)))
model.add(Dense(500, activation='relu'))
model.add(Dense(1, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
```

列表 17.17：更新 MLP 模型以向输入添加噪声的示例。

```
# mlp overfit on the two circles dataset with input noise
```

```
from sklearn.datasets import make_circles
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import GaussianNoise
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_circles(n_samples=100, noise=0.1, random_state=1)
# split into train and test
n_train = 30
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(GaussianNoise(0.01, input_shape=(2,)))
model.add(Dense(500, activation='relu'))
model.add(Dense(1, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=4000, verbose=0)
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

列表 17.18：在两圆问题上向输入添加噪声的 MLP 示例。

运行示例报告模型在训练集和测试数据集上的性能。

注意：由于学习算法的随机性，您的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

在这种情况下，我们可能会看到模型在测试数据集上的性能略有提升，而对训练数据集没有负面影响。

```
Train: 1.000, Test: 0.786
```

列表 17.19：向输入添加噪声的 MLP 在两圆问题上的示例输出。

我们清楚地看到了在训练过程中添加的噪声对模型评估的影响，如线图上所示。噪声导致模型在训练期间的准确率上下波动，可能是由于噪声引入了与训练数据集中的真实点冲突的点。也许更低的输入噪声标准差会更合适。

