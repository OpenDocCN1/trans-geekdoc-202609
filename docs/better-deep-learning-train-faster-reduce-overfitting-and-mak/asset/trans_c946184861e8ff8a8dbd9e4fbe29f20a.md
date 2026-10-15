

```
row_ix = where(y == class_value)
# scatter plot for points with a different color
pyplot.scatter(X[row_ix, 0], X[row_ix, 1])
# show plot
pyplot.show()
```

清单 3.6：绘制 blobs 问题样本的散点图示例。

运行该示例会生成整个数据集的散点图。我们可以看到，标准差为 2.0 意味着这些类别不是线性可分的（无法用一条线分开），这导致了许多有歧义的点。这是我们所期望的，因为它意味着该问题并非微不足道，并且能让神经网络模型找到许多不同的、足够好的候选解。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_67_0.png)

图 3.1：包含三个类别且按类别值着色的 Blobs 数据集散点图。

## 3.3.2 使用批量梯度下降拟合 MLP

我们可以开发一个多层感知器（MLP）模型来解决前一节描述的多分类问题，并使用批量梯度下降对其进行训练。首先，我们需要对目标变量进行独热编码，将整数类别值转换为二进制向量。这将使模型能够预测每个样本属于三个类别中每一个类别的概率，从而在训练模型时提供更细致的预测和上下文。

创建了一个折线图，显示模型在每个训练轮次中的训练集和测试集准确率。这些学习曲线可以说明三件事：模型学习该问题的速度、模型对该问题的学习程度，以及训练期间模型更新的噪声程度。

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

清单 3.12：绘制 MLP 模型学习曲线的示例。

将这些元素组合在一起，完整的示例如下所示。

```
# mlp for the blobs problem with batch gradient descent
from sklearn.datasets.samples_generator import make_blobs
from keras.layers import Dense
from keras.models import Sequential
from keras.optimizers import SGD
from keras.utils import to_categorical
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2, random_state=2)
# one hot encode output variable
y = to_categorical(y)
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(50, input_dim=2, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(3, activation='softmax'))
# compile model
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='categorical_crossentropy', optimizer=opt, metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0,
    batch_size=len(trainX))
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

清单 3.13：在 blobs 问题上对 MLP 使用批量梯度下降的示例。

运行该示例首先会报告模型在训练集和测试集上的性能。

**注意：** 由于学习算法具有随机性，您的具体结果可能会有所不同。建议多次运行该示例并比较平均性能。

在本例中，我们可以看到训练集和测试集的性能相近，分别为 81% 和 83%。

```
Train: 0.814, Test: 0.834
```

清单 3.14：在 blobs 问题上对 MLP 使用批量梯度下降的示例输出。

生成了一个折线图，显示模型在训练集（蓝色）和测试集（橙色）上的损失和分类准确率。我们可以看到，模型学习该问题的速度相对较慢，大约在 100 个轮次后收敛到某个解，之后模型性能的变化很小。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_71_0.png)

图 3.2：使用批量梯度下降拟合的 MLP 在训练集和测试集上的分类准确率折线图。

## 3.3.3 使用随机梯度下降拟合 MLP

上一节中的批量梯度下降示例可以更新为使用随机梯度下降。这需要将批大小从训练数据集的大小改为 1。

```
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0,
    batch_size=1)
```

清单 3.15：配置随机梯度下降的示例。

随机梯度下降要求模型为每个训练样本进行一次预测并更新权重。与批量梯度下降相比，这会显著减慢训练过程。这一改变的预期效果是：模型学习得更快（例如从学习曲线来看），并且对模型的更新是有噪声的，从而反过来导致训练过程中的性能表现带有噪声。包含此更改的完整示例如下所列。

```
# mlp for the blobs problem with stochastic gradient descent
from sklearn.datasets.samples_generator import make_blobs
from keras.layers import Dense
from keras.models import Sequential
from keras.optimizers import SGD
from keras.utils import to_categorical
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2, random_state=2)
# one hot encode output variable
y = to_categorical(y)
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(50, input_dim=2, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(3, activation='softmax'))
# compile model
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='categorical_crossentropy', optimizer=opt, metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0,
                    batch_size=1)
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

清单 3.16：在 blobs 问题上对 MLP 使用随机梯度下降的示例。

运行该示例首先会报告模型在训练集和测试集上的性能。

**注意：** 由于学习算法具有随机性，您的具体结果可能会有所不同。建议多次运行该示例并比较平均性能。

在本例中，我们可以看到训练集和测试集的性能相近，准确率约为 50%，但明显差于使用批量梯度下降的情况（约差 30 个百分点）。至少对于该问题以及所选的模型和模型配置而言，随机（在线）梯度下降并不合适。

```
Train: 0.508, Test: 0.530
```

清单 3.17：在 blobs 问题上对 MLP 使用随机梯度下降的示例输出。

