

运行示例会创建一个散点图，显示每个类别中样本的半圆形或月牙形分布。我们可以看到点分布中的噪声使月牙形状变得不那么明显。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_295_0.png)

图 13.1：月亮数据集的散点图，用颜色显示每个样本的类别值。

这是一个很好的测试问题，因为类别无法用一条线分开，也就是说不是线性可分的，需要像神经网络这样的非线性方法来解决。我们只生成了100个样本，这对神经网络来说很少，提供了过拟合训练数据集并在测试数据集上产生更高误差的机会：这是使用正则化的一个很好的案例。此外，样本带有噪声，使得模型有机会学习样本中无法泛化的方面。

### 13.3.2 过拟合多层感知机模型

我们可以开发一个MLP模型来解决这个二分类问题。该模型将有一个隐藏层，其中包含比解决该问题所需更多的节点，从而提供了过拟合的机会。我们还会将模型训练得比所需时间更长，以确保模型过拟合。在定义模型之前，我们将数据集分为训练集和测试集，使用30个样本训练模型，用70个样本来评估拟合模型的性能。

```
# generate 2d classification dataset
X, y = make_moons(n_samples=100, noise=0.2, random_state=1)
```

```
# split into train and test
n_train = 30
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
```

清单 13.7：准备数据建模的示例。

接下来，我们可以定义模型。模型在隐藏层使用500个节点和修正线性单元（ReLU）激活函数。输出层使用sigmoid激活函数来预测0或1的类别值。模型使用二元交叉熵损失函数进行优化，该函数适用于二分类问题，并使用高效的Adam版本的梯度下降。

```
# define model
model = Sequential()
model.add(Dense(500, input_dim=2, activation='relu'))
model.add(Dense(1, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
```

清单 13.8：为月亮问题定义模型的示例。

然后，所定义的模型在训练数据上拟合4,000个epoch，默认批次大小为32。我们将使用测试集作为验证数据集，以了解模型在训练期间对保留数据集的性能。

```
# fit model
history = model.fit(trainX, trainy, epochs=4000, validation_data=(testX, testy), verbose=0)
```

清单 13.9：为月亮问题拟合模型的示例。

接下来，我们将评估模型在测试数据集上的性能并报告结果。

```
# evaluate the model
_, train_acc = model.evaluate(trainX, trainy, verbose=0)
_, test_acc = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))
```

清单 13.10：为月亮问题评估模型的示例。

最后，我们将绘制模型性能的学习曲线，包括训练期间每个epoch在训练集和测试集上的交叉熵损失和分类准确率。

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

清单 13.11：绘制训练期间模型性能学习曲线的示例。

## 13.3 权重正则化案例研究

我们可以将所有部分组合在一起；完整的示例如下所示。

### 清单 13.12：为双月亮问题拟合MLP的示例。

```
# overfit mlp for the moons dataset
from sklearn.datasets import make_moons
from keras.models import Sequential
from keras.layers import Dense
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_moons(n_samples=100, noise=0.2, random_state=1)
# split into train and test sets
n_train = 30
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(500, input_dim=2, activation='relu'))
model.add(Dense(1, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, epochs=4000, validation_data=(testX, testy), verbose=0)
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

运行示例首先报告模型在训练集和测试集上的性能。我们可以看到模型在训练数据集上的性能优于测试数据集，这是过拟合的一个可能迹象。

注意：由于学习算法的随机性，您的具体结果可能会有所不同。可以考虑多次运行示例并比较平均性能。

### 清单 13.13：在双月亮问题上拟合MLP的示例输出。

```
Train: 1.000, Test: 0.914
```

还创建了折线图，显示每个训练轮次在训练集和测试集上的交叉熵损失和分类准确率的学习曲线。损失的学习曲线显示出明显的过拟合模式，分类准确率的学习曲线也反映了同样的模式。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_298_0.png)

图 13.2：训练期间训练集和测试集上损失和准确率的学习曲线折线图。

### 13.3.3 带权重正则化的MLP模型

我们可以向隐藏层添加权重正则化，以减少模型对训练数据集的过拟合，并提高在保留集上的性能。我们将使用L2向量范数（也称为权重衰减），正则化参数（称为alpha或lambda）设为0.001，这是任意选择的。这可以通过向层添加`kernel_regularizer`参数并将其设置为`l2`的实例来实现。

```
model.add(Dense(500, input_dim=2, activation='relu', kernel_regularizer=l2(0.001)))
```

清单 13.14：使用权重正则化更新的层。

下面列出了在月亮数据集上使用权重正则化拟合和评估模型的更新示例。

```
# mlp with weight regularization for the moons dataset
from sklearn.datasets import make_moons
from keras.models import Sequential
from keras.layers import Dense
from keras.regularizers import l2
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_moons(n_samples=100, noise=0.2, random_state=1)
# split into train and test sets
n_train = 30
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(500, input_dim=2, activation='relu', kernel_regularizer=l2(0.001)))
model.add(Dense(1, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, epochs=4000, validation_data=(testX, testy), verbose=0)
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

清单 13.15：使用权重正则化解决双月亮问题的更新MLP示例。

运行示例首先报告模型在训练集和测试集上的性能。

注意：由于学习算法的随机性，您的具体结果可能会有所不同。可以考虑多次运行示例并比较平均性能。

在这种情况下，我们看到训练数据集上的准确率没有变化，而测试数据集上的准确率有所提高。

```
Train: 1.000, Test: 0.943
```

清单 13.16：使用权重正则化解决双月亮问题的更新MLP的示例输出。

我们会期望，过拟合的标志性学习曲线也会因权重正则化的使用而改变。与测试集上的模型准确率先升后降不同，我们应该看到它在训练过程中持续上升。正如所料，测试数据集上的损失和准确率学习曲线趋于平稳，表明模型不再过拟合训练数据集。

