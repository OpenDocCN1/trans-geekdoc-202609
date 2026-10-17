
```python
from matplotlib import pyplot

# generate regression dataset

X, y = make_regression(n_samples=1000, n_features=20, noise=0.1, random_state=1)

# standardize dataset

X = StandardScaler().fit_transform(X)

y = StandardScaler().fit_transform(y.reshape(len(y),1))[:,0]

# split into train and test

n_train = 500

trainX, testX = X[:n_train, :], X[n_train:, :]

trainy, testy = y[:n_train], y[n_train:]

# define model

model = Sequential()

model.add(Dense(25, input_dim=20, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(1, activation='linear'))

opt = SGD(lr=0.01, momentum=0.9)

model.compile(loss='mean_absolute_error', optimizer=opt, metrics=['mse'])

# fit model

history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=100, verbose=0)

# evaluate the model

_, train_mse = model.evaluate(trainX, trainy, verbose=0)

_, test_mse = model.evaluate(testX, testy, verbose=0)

print('Train: %.3f, Test: %.3f' % (train_mse, test_mse))

# plot loss during training

pyplot.subplot(211)

pyplot.title('Mean Absolute Error Loss', pad=-20)

pyplot.plot(history.history['loss'], label='train')

pyplot.plot(history.history['val_loss'], label='test')

pyplot.legend()

# plot mse during training

pyplot.subplot(212)

pyplot.title('Mean Squared Error', pad=-20)

pyplot.plot(history.history['mean_squared_error'], label='train')

pyplot.plot(history.history['val_mean_squared_error'], label='test')

pyplot.legend()

pyplot.show()
```

清单 4.17：回归问题上 MLP 的均方绝对误差损失示例。

运行示例首先会打印模型在训练集和测试数据集上的均方误差。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_100_0.png)

图 4.4：圆圈二元分类问题的散点图。

点已经在 0 附近合理缩放，几乎在 [-1,1] 范围内。在这种情况下我们不会重新缩放它们。数据集平均分为训练集和测试集。

```python
# split into train and test

n_train = 500

trainX, testX = X[:n_train, :], X[n_train:, :]

trainy, testy = y[:n_train], y[n_train:]
```

清单 4.21：将数据拆分为训练集和测试数据集的示例。

可以定义一个简单的 MLP 模型来解决此问题，该模型期望数据集中的两个特征的两个输入，一个具有 50 个节点的隐藏层、一个整流线性激活函数以及一个输出层，该输出层需要根据损失函数的选择进行配置。

```python
# define model

model = Sequential()

model.add(Dense(50, input_dim=2, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(1, activation='...'))
```

清单 4.22：定义 MLP 模型的示例。

模型将使用随机梯度下降进行拟合，使用合理的默认学习率为 0.01，动量为 0.9。

```python
opt = SGD(lr=0.01, momentum=0.9)
```

```python
model.compile(loss='...', optimizer=opt, metrics=['accuracy'])
```

清单 4.23：编译 MLP 模型的示例。

我们将对模型进行 200 个训练轮次的拟合，并在每个轮次结束时评估模型的损失和准确率，以便我们可以绘制学习曲线。

```python
# fit model

history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0)
```

清单 4.24：拟合 MLP 模型的示例。

现在我们有了问题和模型的基础，我们可以看看评估三种常见的损失函数，这些损失函数适用于二元分类预测建模问题。虽然这些示例中使用了 MLP，但在训练 CNN 和 RNN 模型进行二元分类时也可以使用相同的损失函数。

### 4.3.1 二元交叉熵损失

交叉熵是用于二元分类问题的默认损失函数。它适用于目标值在集合 {0, 1} 中的二元分类。数学上，它是在最大似然推理框架下首选的损失函数。它是首先要评估的损失函数，只有在有充分理由时才更改。交叉熵将计算一个分数，该分数概括了预测类别 1 的实际概率分布与预测概率分布之间的平均差异。该分数最小化，完美的交叉熵值为 0。可以在 Keras 中通过在编译模型时指定 `'binary_crossentropy'` 来指定交叉熵作为损失函数。

```python
model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])
```

清单 4.25：使用二元交叉熵损失的示例。

该函数要求输出层配置为单个节点并使用 `'sigmoid'` 激活，以便预测类别 1 的概率。

```python
model.add(Dense(1, activation='sigmoid'))
```

清单 4.26：使用 sigmoid 激活函数的示例。

MLP 使用交叉熵损失的两个圆圈二元分类问题的完整示例如下所示。

```python
# mlp for the circles problem with cross-entropy loss

from sklearn.datasets import make_circles

from keras.models import Sequential

from keras.layers import Dense

from keras.optimizers import SGD

from matplotlib import pyplot

# generate 2d classification dataset

X, y = make_circles(n_samples=1000, noise=0.1, random_state=1)

# split into train and test

n_train = 500

trainX, testX = X[:n_train, :], X[n_train:, :]

trainy, testy = y[:n_train], y[n_train:]

# define model

model = Sequential()

model.add(Dense(50, input_dim=2, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(1, activation='sigmoid'))

opt = SGD(lr=0.01, momentum=0.9)

model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])

# fit model

history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0)

# evaluate the model

_, train_acc = model.evaluate(trainX, trainy, verbose=0)

_, test_acc = model.evaluate(testX, testy, verbose=0)

print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))

# plot loss during training

pyplot.subplot(211)

pyplot.title('Binary Cross-Entropy Loss', pad=-20)

pyplot.plot(history.history['loss'], label='train')

pyplot.plot(history.history['val_loss'], label='test')

pyplot.legend()

# plot accuracy during training

pyplot.subplot(212)

pyplot.title('Classification Accuracy', pad=-40)

pyplot.plot(history.history['acc'], label='train')

pyplot.plot(history.history['val_acc'], label='test')

pyplot.legend()

pyplot.show()
```

清单 4.27：两个圆圈问题使用二元交叉熵的示例。

运行示例首先会打印模型在训练集和测试数据集上的分类准确率。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

在这种情况下，我们可以看到模型合理地学习了该问题，在训练数据集上实现了约 83% 的准确率，在测试数据集上约为 84%。分数相当接近，表明模型可能既不过拟合也不欠拟合。

```python
Train: 0.834, Test: 0.848
```

清单 4.28：使用二元交叉熵进行两个圆圈问题时的示例输出。

还创建了一个图，显示了两条线图，顶部为训练集（蓝色）和测试集（橙色）在轮次上的交叉熵损失，底部图显示了轮次上的分类准确率。该图显示训练过程收敛良好。损失的图是平滑的，因为概率分布之间的误差是连续的，而准确率的线图显示出波动，因为训练集和测试集中的示例最终只能预测为正确或不正确，从而对性能的反馈较少。

## 4.3. 二元分类损失函数案例研究

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_103_0.png)

Figure 4.5: 关于双圆二元分类问题的训练 epoch 上交叉熵损失和分类准确率的线图。

An alternative to cross-entropy for binary classification problems is the hinge loss function, primarily developed for use with Support Vector Machine (SVM) models. It is intended for use with binary classification where the target values are in the set {-1, 1}. The hinge loss function encourages examples to have the correct sign, assigning more error when there is a difference in the sign between the actual and predicted class values. Reports of performance with the hinge loss are mixed, sometimes resulting in better performance than cross-entropy on binary classification problems. Firstly, the target variable must be modified to have values in the set {-1, 1}.

```python
# change y from {0,1} to {-1,1}

y[where(y == 0)] = -1
```

The hinge loss function can then be specified as `'hinge'` in the compile function.

```python
model.compile(loss='hinge', optimizer=opt, metrics=['accuracy'])
```

Finally, the output layer of the network must be configured to have a single node with a hyperbolic tangent activation function capable of outputting a single value in the range [-1, 1].

```python
model.add(Dense(1, activation='tanh'))
```

Listing 4.31: 使用双曲正切激活函数的示例。

The complete example of an MLP with a hinge loss function for the two circles binary classification problem is listed below.

```python
# mlp for the circles problem with hinge loss

from sklearn.datasets import make_circles

from keras.models import Sequential

from keras.layers import Dense

from keras.optimizers import SGD

from matplotlib import pyplot

from numpy import where

# generate 2d classification dataset

X, y = make_circles(n_samples=1000, noise=0.1, random_state=1)

# change y from {0,1} to {-1,1}

y[where(y == 0)] = -1

# split into train and test

n_train = 500

trainX, testX = X[:n_train, :], X[n_train:, :]

trainy, testy = y[:n_train], y[n_train:]

# define model

model = Sequential()

model.add(Dense(50, input_dim=2, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(1, activation='tanh'))

opt = SGD(lr=0.01, momentum=0.9)

model.compile(loss='hinge', optimizer=opt, metrics=['accuracy'])

# fit model

history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0)

# evaluate the model

_, train_acc = model.evaluate(trainX, trainy, verbose=0)

_, test_acc = model.evaluate(testX, testy, verbose=0)

print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))

# plot loss during training

pyplot.subplot(211)

pyplot.title('Hinge Loss', pad=-20)

pyplot.plot(history.history['loss'], label='train')

pyplot.plot(history.history['val_loss'], label='test')

pyplot.legend()

# plot accuracy during training

pyplot.subplot(212)

pyplot.title('Classification Accuracy', pad=-40)
```
