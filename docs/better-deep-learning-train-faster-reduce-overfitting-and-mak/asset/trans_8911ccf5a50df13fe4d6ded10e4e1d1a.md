
George Dahl 等人在其 2013 年题为 *使用整流线性单元和 dropout 改进深度神经网络用于 LVCSR* 的论文中使用了具有整流线性激活函数和 dropout 的深度神经网络，在当时在标准语音识别任务上取得了最先进的结果。他们使用贝叶斯优化程序来配置激活函数的选择和 dropout 的量。

... 贝叶斯优化程序 learned that dropout 对我们训练的规模的 sigmoid 网络没有帮助。一般来说，ReLU 和 dropout 似乎配合得相当好。

## 16.1.5 使用 Dropout 正则化的技巧

本节提供了使用 dropout 正则化训练神经网络的一些技巧。

### 使用于所有网络类型

Dropout 正则化是一种通用方法。它可用于大多数，也许是所有类型的神经网络模型，尤其是最常见的网络类型，如多层感知器、卷积神经网络和长短期记忆递归神经网络。对于 LSTM 来说，使用不同的 dropout 率用于输入和递归连接可能是可取的。

### Dropout 率

Dropout 超参数的默认解释是训练某一层中给定节点的概率，其中 1.0 表示无 dropout，0.0 表示该层无输出。隐藏层中 dropout 的一个良好值介于 0.5 和 0.8 之间。输入层使用更大的 dropout（保留）率，例如 0.8。

### 使用更大的网络

更大的网络（更多层或更多节点）更容易过拟合训练数据是很常见的。使用 dropout 正则化时，可以使用更大的网络而过拟合风险更低。事实上，可能需要更大的网络（每层更多节点），因为 dropout 会以概率方式降低网络的容量。一个经验法则是将 dropout 前层的节点数除以拟议的 dropout 率，并将其用作使用 dropout 的新网络中的节点数。例如，一个具有 100 个节点且拟议 dropout 率为 0.5 的网络在使用 dropout 时需要 200 个节点（100/0.5）。

> 如果 *n* 是任意层中隐藏单元的数量且 *p* 是保留单元的概率 [...] 一个良好的 dropout 网络应至少有 *n/p* 个单元
>
> — *Dropout：防止神经网络过拟合的简单方法*，2014。

### 网格搜索参数

与其猜测网络合适的 dropout 率，不如系统地测试不同的比率。例如，以 0.1 为增量测试 1.0 到 0.1 之间的值。这将有助于你发现对特定模型和数据集最有效的方法，以及模型对 dropout 率的敏感程度。更敏感的模型可能不稳定，可能需要增大规模。

### 使用权重约束

网络权重会因层激活的概率性移除而增大。较大的权重大小可能是网络不稳定的迹象。为了抵消这种效应，可以施加权重约束，强制某一层中所有权重的范数（大小）低于指定值。例如，推荐使用最大范数约束，其值介于 3 和 4 之间。

> ... 我们可以使用 max-norm 正则化。这将约束每个隐藏单元 incoming 权重向量的范数，使其受常数 c 限制。c 的典型值范围为 3 到 4。
>
> — Dropout：防止神经网络过拟合的简单方法，2014。

这确实引入了一个额外的超参数，可能需要为模型进行调优。

### 使用于较小数据集

与其它正则化方法类似，dropout 在训练数据有限且模型可能过拟合训练数据的问题上更有效。在训练数据量大的问题上，使用 dropout 的收益可能较少。

对于非常大的数据集，正则化带来的泛化误差减少很少。在这些情况下，使用 dropout 和更大模型的计算成本可能超过正则化的收益。

## 16.2 Keras API 中的 Dropout

本节演示如何使用 Keras API 使用 dropout。

### 16.2.1 Keras 中的 Dropout

Keras 支持 dropout 正则化。Keras 中最简单的 dropout 形式由 Dropout 核心层提供。创建时，可以将 dropout 率指定为将该层的每个输入设为零的概率。这与论文中 dropout 率的定义不同，在论文中该比率指的是保留输入的概率。因此，当论文中建议 dropout 率为 0.8（保留 80%）时，实际上将是 dropout 率为 0.2（将 20% 的输入设为零）。下面是创建一个有 50% 机会将输入设为零的 dropout 层的示例。

```python
layer = Dropout(0.5)
```

清单 16.1：创建 Dropout 层的示例。

### 16.2.2 层上的 Dropout

Dropout 层被添加到模型中现有层之间，并应用于被馈送到后续层的先前层的输出。例如，给定两个密集层：

```python
...
model.add(Dense(32))
model.add(Dense(32))
...
```

清单 16.2：两个 Dense 隐藏层的示例。

我们可以在它们之间插入一个 dropout 层，在这种情况下，第一层的输出或激活值会应用 dropout，然后作为下一层的输入。

```python
...
model.add(Dense(32))
model.add(Dropout(0.5))
model.add(Dense(32))
...
```

清单 16.3：两个 Dense 隐藏层之间 Dropout 层的示例。

Dropout 也可以应用于可见层，例如网络的输入。这要求你将网络定义为以 Dropout 层作为第一层，并向该层添加 input_shape 参数以指定输入样本的预期形状。

```python
...
model.add(Dropout(0.5, input_shape=(2,)))
...
```

清单 16.4：Dropout 输入层的示例。

让我们看看 dropout 正则化如何与一些常见网络类型一起使用。

### MLP Dropout 正则化

下面的示例在两个 Dense 全连接层之间添加 dropout。

```python
# example of dropout between fully connected layers
from keras.layers import Dense
from keras.layers import Dropout
...
model.add(Dense(32))
model.add(Dropout(0.5))
model.add(Dense(1))
...
```

清单 16.5：MLP 的 Dropout 示例。

### CNN Dropout 正则化

Dropout 可在卷积层（例如 Conv2D）之后以及池化层（例如 MaxPooling2D）之后使用。通常，dropout 仅在池化层之后使用，但这只是一个粗略的启发式方法。

```python
# example of dropout for a CNN
from keras.layers import Dense
from keras.layers import Conv2D
from keras.layers import MaxPooling2D
from keras.layers import Dropout
...
model.add(Conv2D(32, (3,3)))
model.add(Conv2D(32, (3,3)))
model.add(MaxPooling2D())
model.add(Dropout(0.5))
model.add(Dense(1))
...
```

清单 16.6：CNN 的 Dropout 示例。

在这种情况下，dropout 应用于特征图中的每个元素或单元。使用 dropout 与卷积神经网络的另一种方法是丢弃卷积层的整个特征图，然后在池化期间不使用它们。这称为空间 dropout（或 Spatial Dropout）。

> 相反，我们提出了一种新的 dropout 方法，我们称之为 SpatialDropout。对于给定的卷积特征张量 [...] [我们] 将 dropout 值扩展到整个特征图。
>
> — 使用卷积网络进行高效目标定位，2015。

Spatial Dropout 在 Keras 中通过 SpatialDropout2D 层提供（以及 1D 和 3D 版本）。

```python
# example of spatial dropout for a CNN
from keras.layers import Dense
from keras.layers import Conv2D
from keras.layers import MaxPooling2D
from keras.layers import SpatialDropout2D
...
model.add(Conv2D(32, (3,3)))
model.add(Conv2D(32, (3,3)))
model.add(SpatialDropout2D(0.5))
model.add(MaxPooling2D())
model.add(Dense(1))
...
```

清单 16.7：CNN 的 Spatial Dropout 示例。

### RNN Dropout 正则化

下面的示例在两个层之间添加 dropout：一个 LSTM 递归层和一个 Dense 全连接层。
