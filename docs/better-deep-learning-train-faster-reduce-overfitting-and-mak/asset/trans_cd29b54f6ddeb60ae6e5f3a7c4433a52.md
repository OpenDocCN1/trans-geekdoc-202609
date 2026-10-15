
### 2.2.1 配置模型节点

层的第一个参数指定了该层使用的节点数。 多层感知机（Multilayer Perceptron，或 MLP）模型的全连接层通过 Dense 层添加。 例如，我们可以按如下方式创建一个具有 32 个节点 的全连接层：

```
...
layer = Dense(32)
```

清单 2.1：指定 Dense 层节点数的示例。

同样地，循环神经网络层的节点数也可以以相同的方式指定。 例如，我们可以按如下方式创建一个具有 32 个节点（或单元）的 LSTM 层：

```
...
layer = LSTM(32)
```

清单 2.2：指定 LSTM 层节点数的示例。

卷积神经网络（Convolutional neural networks，或 CNNs）没有节点，而是指定滤波器映射的数量和形状。 滤波器映射的数量和大小定义了层的容量。 我们可以按如下方式定义一个具有 32 个滤波器映射的二维 CNN，每个滤波器映射的大小为 3×3：

```
...
layer = Conv2D(32, (3,3))
```

清单 2.3：指定 CNN 层滤波器映射数量的示例。

### 2.2.2 配置模型层

层通过调用 add() 函数并传入层来添加到顺序模型中。 MLP 的全连接层可以通过重复调用 add() 函数并传入已配置的 Dense 层来添加；例如：

```
...
model = Sequential()
model.add(Dense(32))
model.add(Dense(64))
```

清单 2.4：指定 MLP 层数的示例。

同样地，循环网络的层数也可以以相同的方式添加，以形成堆叠的循环模型。 一个重要的区别是循环层期望三维输入，因此先前的循环层必须返回输出序列的完整序列，而不是在输入序列末尾每个节点的单个输出。 这可以通过将 return_sequences 参数设置为 True 来实现。 例如：

```
...
model = Sequential()
model.add(LSTM(32, return_sequences=True))
model.add(LSTM(32))
```

清单 2.5：指定 LSTM 层数的示例。

卷积层可以直接堆叠，通常将一到两个卷积层堆叠在一起，然后跟一个池化层，然后重复这种层模式；例如：

```
...
model = Sequential()
model.add(Conv2D(16, (3,3)))
model.add(Conv2D(16, (3,3)))
model.add(MaxPooling2D((2,2)))
model.add(Conv2D(32, (3,3)))
model.add(Conv2D(32, (3,3)))
model.add(MaxPooling2D((2,2)))
```

清单 2.6：指定 CNN 层数的示例。

现在我们知道了如何在 Keras 中配置模型的节点数和层数，我们可以看看容量如何影响模型在多类分类问题上的性能。

## 2.3 模型容量案例研究

在本节中，我们将演示如何使用模型容量来控制 MLP 在简单分类问题上的学习。 此示例为使用您自己的神经网络探索分类和回归问题的模型容量提供了一个模板。

### 2.3.1 多类分类问题

我们将使用标准的多类分类问题作为基础来演示模型容量对模型性能的影响。 scikit-learn 类提供了 make_blobs() 函数，可用于创建具有规定样本数、输入变量、类别数以及类内样本方差的多类分类问题。 我们可以通过 n_features 参数配置问题具有特定数量的输入变量，并通过 centers 参数配置特定数量的类别或中心。 random_state 可用于为伪随机数生成器设置种子，以确保每次调用函数时始终获得相同的样本。 例如，下面的调用为具有两个输入变量的三个类别问题生成 1,000 个示例。

```
...
# generate 2d classification dataset
X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2, random_state=2)
```

清单 2.7：为 blobs 问题创建样本的示例。

结果是我们可以建模的数据集的输入和输出元素。 为了感受问题的复杂性，我们可以将每个点绘制在二维散点图上，并按类别值对每个点着色。 完整示例如下所示。

```
# scatter plot of blobs dataset
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

清单 2.8：绘制 blobs 问题样本的示例。

运行示例会创建整个数据集的散点图。 我们可以看到，所选的标准差 2.0 意味着类别不是线性可分的（可由直线分隔），导致许多模糊点。 这是理想的，因为这意味着问题是非平凡的，并且神经网络模型可以找到许多足够好的候选解决方案。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_52_0.png)

图 2.1：具有三个类别且按类别值着色的点的 Blobs 数据集散点图。

为了探索模型容量，我们需要比三个类别和两个变量更复杂的问题。 为了以下实验的目的，我们将使用 100 个输入特征和 20 个类别；例如：

```
...
# generate 2d classification dataset
X, y = make_blobs(n_samples=1000, centers=20, n_features=100, cluster_std=2, random_state=2)
```

清单 2.9：为 blobs 问题创建大量样本的示例。

### 2.3.2 使用节点更改模型容量

在本节中，我们将为 blobs 多类分类问题开发一个多层感知机模型（Multilayer Perceptron，或 MLP），并演示节点数量对模型学习能力的影响。 我们可以先开发一个函数来准备数据集。 数据集的输入和输出元素可以使用上一节中描述的 make_blobs() 函数创建。 接下来，目标变量必须进行独热编码。 这样模型就可以学习预测输入示例属于 20 个类别中每个类别的概率。 我们可以使用 to_categorical() Keras 实用函数来实现此目的，例如：

```
# one hot encode output variable
y = to_categorical(y)
```

清单 2.10：对目标变量进行独热编码的示例。

接下来，我们可以将 1,000 个示例分成两半，使用 500 个示例作为训练数据集，500 个用于评估模型。

```
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
return trainX, trainy, testX, testy
```

清单 2.11：为建模准备数据集的示例。

下面的 create_dataset() 函数将这些元素结合在一起，并以输入和输出元素的形式返回训练集和测试集。

```
# prepare multiclass classification dataset
def create_dataset():
    # generate 2d classification dataset
    X, y = make_blobs(n_samples=1000, centers=20, n_features=100, cluster_std=2,
        random_state=2)
    # one hot encode output variable
    y = to_categorical(y)
    # split into train and test
    n_train = 500
    trainX, testX = X[:n_train, :], X[n_train:, :]
    trainy, testy = y[:n_train], y[n_train:]
    return trainX, trainy, testX, testy
```

清单 2.12：定义用于为建模准备数据集的函数的示例。

我们可以调用此函数来准备数据集。

```
# prepare dataset
trainX, trainy, testX, testy = create_dataset()
```

清单 2.13：准备数据集的示例。

接下来，我们可以定义一个函数，该函数将创建模型，在训练数据集上拟合它，然后在测试数据集上评估它。 模型需要知道输入变量的数量以配置输入层，并需要知道目标类别的数量以配置输出层。 这些属性可以直接从训练数据集中提取。
