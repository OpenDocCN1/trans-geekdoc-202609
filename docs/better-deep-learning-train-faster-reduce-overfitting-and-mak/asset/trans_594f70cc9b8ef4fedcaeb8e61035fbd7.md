
```
pyplot.scatter(X[row_ix, 0], X[row_ix, 1])
# show plot
pyplot.show()
```

列表 24.2: 从 blobs 问题中绘制样本的示例。

运行该示例会创建整个数据集的散点图。我们可以看到，标准差为 2.0 意味着类别不是线性可分的（可由一条直线分隔），导致存在许多模糊点。这是理想的，因为这意味着问题是非平凡的，并且会允许神经网络模型找到许多不同的足够好的候选解，从而导致高方差。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_495_0.png)

图 24.1: 具有三个类别且按类别值着色的 Blobs 数据集散点图。

## 24.2.2 多层感知器模型

在定义模型之前，我们需要设计一个适合集成的问题。在我们的问题中，训练数据集相对较小。具体来说，训练数据集中示例与保留数据集的比例为 10:1。这模拟了一种情况，即我们可能拥有大量未标记的示例和少量用于训练模型的标记示例。我们将从 blobs 问题中创建 1,100 个数据点。模型将在前 100 个点上训练，剩余的 1,000 个点将被保留在测试数据集中，模型无法使用。

该问题是一个多类分类问题，我们将使用输出层的 softmax 激活函数对其建模。这意味着模型将预测一个具有三个元素的向量，表示样本属于三个类别中每个类别的概率。因此，在将行拆分为训练集和测试集之前，我们必须对类别值进行独热编码。我们可以使用 Keras 的 to_categorical() 函数来完成此操作。

```
# generate 2d classification dataset
X, y = make_blobs(n_samples=1100, centers=3, n_features=2, cluster_std=2, random_state=2)
# one hot encode output variable
y = to_categorical(y)
# split into train and test
n_train = 100
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
```

列表 24.3: 准备数据集用于建模的示例。

接下来，我们可以定义和编译模型。模型将期望具有两个输入变量的样本。模型然后有一个包含 25 个节点且使用整流线性激活函数的单个隐藏层，然后是一个包含三个节点以预测每个类别的概率并使用 softmax 激活函数的输出层。由于问题是多类的，我们将使用分类交叉熵损失函数来优化模型，并使用较小的学习率和动量的随机梯度下降。

```
# define model
model = Sequential()
model.add(Dense(25, input_dim=2, activation='relu'))
model.add(Dense(3, activation='softmax'))
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='categorical_crossentropy', optimizer=opt, metrics=['accuracy'])
```

列表 24.4: 定义 MLP 模型的示例。

模型将拟合 200 个训练 epoch，我们将在每个 epoch 上在测试集上评估模型，将测试集用作验证集。

```
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0)
```

列表 24.5: 拟合 MLP 模型的示例。

运行结束时，我们将在训练集和测试集上评估模型的性能。

```
# evaluate the model
_, train_acc = model.evaluate(trainX, trainy, verbose=0)
_, test_acc = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))
```

列表 24.6: 评估 MLP 模型的示例。

最后，我们将在训练和验证数据集上绘制模型准确率随每个训练 epoch 的学习曲线。

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

列表 24.7: 为 MLP 绘制学习曲线的示例。

将所有这些结合起来，完整的示例如下所示。

```
# develop an mlp for blobs dataset
from sklearn.datasets.samples_generator import make_blobs
from keras.utils import to_categorical
from keras.models import Sequential
from keras.layers import Dense
from keras.optimizers import SGD
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_blobs(n_samples=1100, centers=3, n_features=2, cluster_std=2, random_state=2)
# one hot encode output variable
y = to_categorical(y)
# split into train and test
n_train = 100
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(25, input_dim=2, activation='relu'))
model.add(Dense(3, activation='softmax'))
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='categorical_crossentropy', optimizer=opt, metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0)
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

列表 24.8: 在 blobs 问题上拟合 MLP 的示例。

运行该示例会打印最终模型在训练集和测试集上的性能。

注意：由于学习算法的随机性，您的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

在这种情况下，我们可以看到模型在训练数据集上实现了约 82% 的准确率，我们知道这是乐观的，而在测试数据集上约为 79%，我们期望这更现实。

```
Train: 0.820, Test: 0.791
```

列表 24.9: 在 blobs 问题上拟合 MLP 的示例输出。

还创建了一条线图，显示模型在每个训练 epoch 上在训练集和测试集上的准确率学习曲线。我们可以看到，正如我们在最终得分中所指出的那样，在运行的大部分时间里，训练准确率更为乐观。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_498_0.png)

图 24.2: 模型在训练集和测试数据集上每个训练 epoch 的准确率学习曲线线图。

接下来，我们可以看看如何实现一个激进的学习率调度。

## 24.2.3 余弦退火学习率

有效的快照集成需要使用激进的学习率调度训练神经网络。余弦退火调度是激进学习率调度的一个例子，其中学习率从高开始并相对迅速地下降到接近零的最小值，然后再次增加到最大值。我们可以按照 2017 年论文 *快照集成：训练 1 次，免费获得 M 次* 中描述的方式实现该调度。该方程需要总训练 epoch、最大学习率和周期数作为参数，以及当前 epoch 编号。然后函数返回给定 epoch 的学习率。

$$\alpha(t) = \frac{\alpha_0}{2} \left( \cos\left( \frac{\pi\,\text{mod}(t-1,\lceil T/M\rceil)}{\lceil T/M\rceil} \right) + 1 \right)$$

图 24.3: 余弦退火学习率调度的方程。

其中 $a(t)$ 是 epoch $t$ 时的学习率，$a_0$ 是最大学习率，$T$ 是总 epoch 数，$M$ 是周期数，$mod$ 是取模运算，方括号表示向下取整运算。下面的函数 `cosine_annealing()` 实现了该方程。

```python
# cosine annealing learning rate schedule
def cosine_annealing(epoch, n_epochs, n_cycles, lrate_max):
    epochs_per_cycle = floor(n_epochs/n_cycles)
    cos_inner = (pi * (epoch % epochs_per_cycle)) / (epochs_per_cycle)
    return lrate_max/2 * (cos(cos_inner) + 1)
```

列表 24.10: 计算余弦退火学习率调度的函数的示例。

我们可以通过绘制 100 个 epoch、五个周期（例如每个 20 个 epoch 长）且最大学习率为 0.01 的学习率来测试此实现。完整的示例如下所示。

```python
# example of a cosine annealing learning rate schedule
from matplotlib import pyplot
from math import pi
from math import cos
from math import floor

# cosine annealing learning rate schedule
def cosine_annealing(epoch, n_epochs, n_cycles, lrate_max):
    epochs_per_cycle = floor(n_epochs/n_cycles)
    cos_inner = (pi * (epoch % epochs_per_cycle)) / (epochs_per_cycle)
    return lrate_max/2 * (cos(cos_inner) + 1)

# create learning rate series
n_epochs = 100
n_cycles = 5
lrate_max = 0.01
series = [cosine_annealing(i, n_epochs, n_cycles, lrate_max) for i in range(n_epochs)]
# plot series
pyplot.plot(series)
```
