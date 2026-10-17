
### Listing 5.7: Keras 中 Adagrad 优化器的示例。

### Adam 优化器

```python
from keras.optimizers import Adam

...

opt = Adam()

model.compile(..., optimizer=opt)
```

Listing 5.8: Keras 中 Adam 优化器的示例。

#### 5.3 学习率案例研究

在本节中，我们将演示如何使用学习率通过 MLP 在一个简单的分类问题上控制收敛。此示例为使用您自己的神经网络探索分类和回归问题的学习率提供了一个模板。

##### 5.3.1 多类分类问题

我们将使用一个小型多类分类问题作为基础来演示学习率对模型性能的影响。`scikit-learn` 类提供了 `make_blobs()` 函数，可用于创建具有规定样本数、输入变量、类别数以及类内样本方差的多类分类问题。该问题可以配置为具有两个输入变量（表示点的 x 和 y 坐标），并且每个组内点的标准差为 2.0。我们将使用相同的随机状态（伪随机数生成器的种子），以确保我们始终获得相同的数据点。

```python
# generate 2d classification dataset

X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2, random_state=2)
```

> Listing 5.9: 创建 blobs 问题样本的示例。

结果是我们可建模的数据集的输入和输出元素。为了感受问题的复杂性，我们可以在二维散点图上绘制每个点，并按类别值对每个点着色。完整示例如下所示。

```python
from sklearn.datasets.samples_generator import make_blobs

from matplotlib import pyplot

from numpy import where

# generate 2d classification dataset

X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2, random_state=2)

# scatter plot for each class value
for class_value in range(3):
    # select indices of points with the class label
    row_ix = where(y == class_value)
    # scatter plot for points with a different color
    pyplot.scatter(X[row_ix, 0], X[row_ix, 1])
    # show plot
    pyplot.show()
```

> Listing 5.10: 绘制 blobs 问题样本的示例。

运行示例会创建整个数据集的散点图。我们可以看到，标准差为 2.0 意味着类别不是线性可分的（可由一条线分隔），导致存在许多模糊点。这是理想的，因为这意味着问题是非平凡的，并且神经网络模型可以找到许多足够好的候选解决方案。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_131_0.png)

Figure 5.1: 散点图：具有三个类别且按类别值着色的 Blobs 数据集。

##### 5.3.2 学习率和动量的影响

在本节中，我们将开发一个多层感知器（MLP）模型来解决 blobs 分类问题，并研究不同学习率和动量的影响。

#### 学习率动态

第一步是开发一个函数来创建问题样本并将其拆分为训练集和测试集。此外，我们还必须对目标变量进行独热编码，以便我们可以开发一个模型来预测示例属于每个类别的概率。下面的 `prepare_data()` 函数实现了此行为，返回拆分为输入和输出元素的训练集和测试集。

```python
# prepare train and test dataset
def prepare_data():
    # generate 2d classification dataset
    X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2, random_state=2)
    # one hot encode output variable
    y = to_categorical(y)
    # split into train and test
    n_train = 500
    trainX, testX = X[:n_train, :], X[n_train:, :]
    trainy, testy = y[:n_train], y[n_train:]
    return trainX, trainy, testX, testy
```

Listing 5.11: 用于准备建模数据集的函数的示例。

接下来，我们可以开发一个函数来拟合和评估 MLP 模型。首先，我们将定义一个简单的 MLP 模型，该模型期望来自 blobs 问题的两个输入变量，具有一个包含 50 个节点的隐藏层，以及一个包含三个节点的输出层，用于预测每个类别的概率。隐藏层中的节点将使用整流线性激活函数，而输出层中的节点将使用 softmax 激活函数。

```python
# define model
model = Sequential()
model.add(Dense(50, input_dim=2, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(3, activation='softmax'))
```

Listing 5.12: 定义 MLP 模型的示例。

我们将使用随机梯度下降优化器，并要求指定学习率，以便我们可以评估不同的速率。模型将训练以最小化交叉熵。

```python
# compile model
opt = SGD(lr=lrate)
model.compile(loss='categorical_crossentropy', optimizer=opt, metrics=['accuracy'])
```

Listing 5.13: 编译 MLP 模型的示例。

模型将拟合 200 个训练轮次，通过少量试错确定，并且测试集将用作验证数据集，以便我们了解训练期间模型的泛化误差。

```python
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0)
```

Listing 5.14: 拟合 MLP 模型的示例。

拟合后，我们将绘制模型在训练轮次上在训练集和测试集上的准确率。

```python
# plot learning curves
pyplot.plot(history.history['acc'], label='train')
pyplot.plot(history.history['val_acc'], label='test')
pyplot.title('lrate='+str(lrate), pad=-50)
```

Listing 5.15: 绘制 MLP 模型学习曲线的示例。

下面的 `fit_model()` 函数将这些元素联系在一起，并将根据训练集和测试集以及要评估的特定学习率拟合模型并绘制其性能。

```python
# fit a model and plot learning curve
def fit_model(trainX, trainy, testX, testy, lrate):
    # define model
    model = Sequential()
    model.add(Dense(50, input_dim=2, activation='relu', kernel_initializer='he_uniform'))
    model.add(Dense(3, activation='softmax'))
    # compile model
    opt = SGD(lr=lrate)
    model.compile(loss='categorical_crossentropy', optimizer=opt, metrics=['accuracy'])
    # fit model
    history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0)
    # plot learning curves
    pyplot.plot(history.history['acc'], label='train')
    pyplot.plot(history.history['val_acc'], label='test')
    pyplot.title('lrate='+str(lrate), pad=-50)
```

Listing 5.16: 定义用于拟合和评估 MLP 模型的函数的示例。

我们现在可以研究不同学习率对模型训练和测试准确率的动态影响。在此示例中，我们将在对数尺度上从 1E-0（1.0）到 1E-7 评估学习率，并通过调用 `fit_model()` 函数为每个学习率创建线图。

```python
# create learning curves for different learning rates
learning_rates = [1E-0, 1E-1, 1E-2, 1E-3, 1E-4, 1E-5, 1E-6, 1E-7]
for i in range(len(learning_rates)):
    # determine the plot number
    plot_no = 420 + (i+1)
    pyplot.subplot(plot_no)
    # fit model and plot learning curves for a learning rate
    fit_model(trainX, trainy, testX, testy, learning_rates[i])
# show learning curves
pyplot.show()
```

Listing 5.17: 评估一系列不同学习率的示例。

将所有这些联系起来，完整示例如下所示。

```python
# study of learning rate on accuracy for blobs problem
from sklearn.datasets.samples_generator import make_blobs
from keras.layers import Dense
from keras.models import Sequential
from keras.optimizers import SGD
from keras.utils import to_categorical
from matplotlib import pyplot

# prepare train and test dataset
def prepare_data():
    # generate 2D classification dataset
    X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2, random_state=2)
    # one hot encode output variable
    y = to_categorical(y)
    # split into train and test
    n_train = 500
    trainX = X[:n_train, :]
    testX = X[n_train:, :]
    trainy = y[:n_train]
    testy = y[n_train:]
    return trainX, trainy, testX, testy

# fit a model and plot learning curve
def fit_model(trainX, trainy, testX, testy, lrate):
    # define model
    model = Sequential()
    model.add(Dense(50, input_dim=2, activation='relu', kernel_initializer='he_uniform'))
    model.add(Dense(3, activation='softmax'))
    # compile model
    opt = SGD(lr=lrate)
    model.compile(loss='categorical_crossentropy', optimizer=opt, metrics=['accuracy'])
    # fit model
    history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0)
    # plot learning curves
    pyplot.plot(history.history['acc'], label='train')
    pyplot.plot(history.history['val_acc'], label='test')
    pyplot.title('lrate='+str(lrate), pad=-50)
    # show learning curves
    pyplot.show()
```

```python
opt = SGD(lr=lrate)
model.compile(loss='categorical_crossentropy', optimizer=opt, metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=200, verbose=0)
# plot learning curves
pyplot.plot(history.history['acc'], label='train')
pyplot.plot(history.history['val_acc'], label='test')
pyplot.title('lrate='+str(lrate), pad=-50)
# prepare dataset
trainX, trainy, testX, testy = prepare_data()
# create learning curves for different learning rates
learning_rates = [1E-0, 1E-1, 1E-2, 1E-3, 1E-4, 1E-5, 1E-6, 1E-7]
for i in range(len(learning_rates)):
    # determine the plot number
    plot_no = 420 + (i+1)
    pyplot.subplot(plot_no)
    # fit model and plot learning curves for a learning rate
    fit_model(trainX, trainy, testX, testy, learning_rates[i])
# show learning curves
pyplot.show()
```

Listing 5.18: 对 MLP 在 blobs 问题上评估一系列不同学习率动态的示例。

运行该示例会创建一个包含八个不同评估学习率的折线图的单一图形。训练数据集上的分类准确率用蓝色标记，而测试数据集上的准确率用橙色标记。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。建议多次运行示例并比较平均性能。

图表显示了学习率过大为 1.0 时行为的振荡，以及学习率过小为 1E-6 和 1E-7 时模型无法学习任何东西的情况。我们可以看到，使用学习率 1E-1、1E-2 和 1E-3 时模型能够很好地学习该问题，尽管随着学习率的降低学习速度逐渐变慢。在所选模型配置下，结果表明适中的学习率 0.1 可在训练集和测试集上获得良好的模型性能。

```python
# plot learning curves
pyplot.plot(history.history['acc'], label='train')
pyplot.plot(history.history['val_acc'], label='test')
pyplot.title('momentum='+str(momentum), pad=-80)
```

Listing 5.19: 评估具有不同动量值的 MLP 的更新函数示例。

通常使用接近 1.0 的动量值，例如 0.9 和 0.99。在本示例中，我们将演示无动量模型的动态与动量值为 0.5 及更高动量值模型的对比。

```python
# create learning curves for different momentums
momentums = [0.0, 0.5, 0.9, 0.99]
for i in range(len(momentums)):
    # determine the plot number
    plot_no = 220 + (i+1)
```
