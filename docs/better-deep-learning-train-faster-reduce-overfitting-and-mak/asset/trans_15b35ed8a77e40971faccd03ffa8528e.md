
## 不要与 Dropout 结合使用

批归一化提供了一定的正则化效果，可降低泛化误差，或许不再需要使用 dropout 进行正则化。

从修改后的 BN-Inception 中移除 Dropout 可加快训练速度，而不会增加过拟合。

> — Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift, 2015.

此外，在同一网络中同时使用批归一化和 dropout 可能不是一个好主意。原因是在 dropout 过程中随机丢弃节点时，用于归一化前一层激活值的统计数据可能会变得嘈杂。

批归一化有时也会降低泛化误差并允许省略 dropout，这是由于用于归一化每个变量的统计量估计中的噪声。

> — Page 425, Deep Learning, 2016.

## 9.2 Keras API 中的批归一化

本节演示如何使用 Keras API 使用批归一化。

### 9.2.1 Keras 中的批归一化

Keras 通过 BatchNormalization 层提供对批归一化的支持。例如：

```
bn = BatchNormalization()
```

编号 9.1：创建批归一化层的示例。

该层将转换输入使其标准化，即均值为零，标准差为一。在训练期间，该层会跟踪每个输入变量的统计数据并使用它们来标准化数据。此外，标准化后的输出可以使用学习到的 Beta 和 Gamma 参数进行缩放，这些参数定义了转换输出的新均值和标准差。该层可以通过 center 和 scale 属性分别配置以控制是否使用这些额外参数。默认情况下，它们是启用的。

用于执行标准化的统计数据，例如每个变量的均值和标准差，会针对每个小批量进行更新并维护一个运行平均值。momentum 参数允许您控制在计算更新时包含多少来自之前小批量的统计数据。默认情况下，该值保持较高，为 0.99。可以将其设置为 0.0 以仅使用当前小批量的统计数据，如原始论文所述。

```
bn = BatchNormalization(momentum=0.0)
```

编号 9.2：创建带动量的批归一化层的示例。

在训练结束时，该层此时的均值和标准差统计数据将在模型用于进行预测时用于标准化输入。默认配置估计所有小批量中的均值和标准差可能是合理的。

### 9.2.2 模型中的 BatchNormalization

批归一化可以在模型的大多数位置使用，并且适用于大多数类型的深度学习神经网络。

### 输入和隐藏层输入

BatchNormalization 层可以添加到您的模型中以标准化原始输入变量或隐藏层的输出。批归一化不建议作为模型适当数据准备的替代方案。尽管如此，当用于标准化原始输入变量时，该层必须指定 input_shape 参数；例如：

```
...
model = Sequential()
model.add(BatchNormalization(input_shape=(2,)))
...
```

编号 9.3：输入批归一化的示例。

当用于标准化隐藏层的输出时，该层可以像其他任何层一样添加到模型中。

```
...
model = Sequential()
...
model.add(BatchNormalization())
...
```

编号 9.4：隐藏层之间批归一化的示例。

### 在激活函数之前或之后使用

BatchNormalization 层可用于在前一层的激活函数之前或之后标准化输入。介绍该方法的原始论文建议在前一层的激活函数之前添加批归一化，例如：

```
...
model = Sequential()
model.add(Dense(32))
model.add(BatchNormalization())
model.add(Activation('relu'))
...
```

编号 9.5：在激活函数之前使用批归一化的示例。

一些报道的实验表明，在前一层的激活函数之后添加批归一化层时性能更好；例如：

```
...
model = Sequential()
model.add(Dense(32, activation='relu'))
model.add(BatchNormalization())
...
```

> 编号 9.6：在激活函数之后使用批归一化的示例。

如果时间和资源允许，值得在您的模型上测试这两种方法并使用性能最佳的方法。让我们看看批归一化如何与一些常见的网络类型一起使用。

下面的示例在 Dense 隐藏层之间在激活函数之后添加批归一化。

```
# example of batch normalization for an mlp
from keras.layers import Dense
from keras.layers import BatchNormalization
...
model.add(Dense(32, activation='relu'))
model.add(BatchNormalization())
model.add(Dense(1))
...
```

> 编号 9.7：MLP 模型批归一化的示例。

下面的示例在卷积层和最大池化层之间在激活函数之后添加批归一化。

```
# example of batch normalization for an cnn
from keras.layers import Dense
from keras.layers import Conv2D
from keras.layers import MaxPooling2D
from keras.layers import BatchNormalization
...
model.add(Conv2D(32, (3,3), activation='relu'))
model.add(BatchNormalization())
model.add(MaxPooling2D())
model.add(Dense(1))
...
```

> 编号 9.8：CNN 模型批归一化的示例。

下面的示例在 LSTM 和 Dense 隐藏层之间在激活函数之后添加批归一化。

```
# example of batch normalization for a lstm
from keras.layers import Dense
from keras.layers import LSTM
from keras.layers import BatchNormalization
...
model.add(LSTM(32))
model.add(BatchNormalization())
model.add(Dense(1))
...
```

编号 9.9：LSTM 模型批归一化的示例。

## 9.3 批归一化案例研究

在本节中，我们将演示如何使用批归一化加速 MLP 在简单二分类问题上的训练。此示例为将批归一化应用于您自己的神经网络以解决分类和回归问题提供了模板。

### 9.3.1 二分类问题

我们将使用一个标准二分类问题，该问题定义了两个二维同心圆的观测值，每个类别一个圆。每个观测值有两个相同尺度的输入变量和一个类别输出值，为 0 或 1。该数据集因绘图时每个类别中观测值的形状而被称为 circles 数据集。我们可以使用 make_circles() 函数从该问题生成观测值。我们将向数据添加噪声并为随机数生成器设置种子，以便每次运行代码时生成相同的样本。

```
# generate 2d classification dataset
X, y = make_circles(n_samples=1000, noise=0.1, random_state=1)
```

编号 9.10：为 circles 问题生成样本的示例。

我们可以绘制数据集，其中两个变量作为图表上的 x 和 y 坐标，类别值作为观测值的颜色。生成数据集并绘制它的完整示例如下所示。

```
# scatter plot of the circles dataset with points colored by class
from sklearn.datasets import make_circles
from numpy import where
from matplotlib import pyplot
# generate circles
X, y = make_circles(n_samples=1000, noise=0.1, random_state=1)
# select indices of points with each class label
for i in range(2):
    samples_ix = where(y == i)
    pyplot.scatter(X[samples_ix, 0], X[samples_ix, 1], label=str(i))
pyplot.legend()
pyplot.show()
```

编号 9.11：绘制 circles 问题样本的示例。
