
你还应该将标签向量化，这很简单：

```python
y_train = np.asarray(train_labels).astype("float32")
y_test = np.asarray(test_labels).astype("float32")
```

现在数据已准备好输入神经网络。

## 4.1.3 构建你的模型

输入数据是向量，而标签是标量（1 和 0）：这是你会遇到的最简单的问题设置之一。在处理此类问题时表现良好的一种模型是简单堆叠的带有 relu 激活函数的全连接（Dense）层。

关于这样一堆 Dense 层，有两个关键的架构决策需要做出：

- 使用多少层
- 每层选择多少个单元

在第 5 章中，你将学习指导你做出这些选择的正式原则。暂时，你需要相信我对以下架构选择的判断：

- 两个中间层，每层 16 个单元
- 第三层将输出关于当前评论情感的标量预测

图 4.1 展示了模型的样子。以下清单展示了 Keras 实现，类似于你之前看到的 MNIST 示例。

![](img/ab452ecf572a1f1372915be13bd8088f_123_0.png)

### 清单 4.4 模型定义

```python
from tensorflow import keras
from tensorflow.keras import layers

model = keras.Sequential([
    layers.Dense(16, activation="relu"),
    layers.Dense(16, activation="relu"),
    layers.Dense(1, activation="sigmoid")
])
```

传递给每个 Dense 层的第一个参数是该层中的单元数：即该层的表示空间维度。你记得从第 2 章和第 3 章中，每个这样的带有 relu 激活的 Dense 层实现以下一系列张量操作：

```
output = relu(dot(input, W) + b)
```

拥有 16 个单元意味着权重矩阵 W 的形状将是 (input_dimension, 16)：与 W 的点积将输入数据投影到一个 16 维的表示空间中（然后你将加上偏置向量 b 并应用 relu 操作）。你可以直观地将表示空间的维度理解为“当学习内部表示时，你允许模型拥有多少自由度”。拥有更多单元（更高维度的表示空间）允许你的模型学习更复杂的表示，但这会使模型在计算上更昂贵，并可能导致学习不需要的模式（即在训练数据上能提升性能但在测试数据上无法提升性能的模式）。

中间层使用 relu 作为激活函数，而最后一层使用 sigmoid 激活以输出一个概率（一个 0 到 1 之间的分数，表示样本具有目标“1”的可能性：评论是正面的可能性）。relu（修正线性单元）是一种旨在将负值置零的函数（参见图 4.2），而 sigmoid 则将任意值“压缩”到 [0, 1] 区间内（参见图 4.3），输出可以解释为概率的内容。

![](img/ab452ecf572a1f1372915be13bd8088f_124_0.png)

**图 4.2** 修正线性单元函数

最后，你需要选择损失函数和优化器。因为你面对的是二分类问题，且模型输出是一个概率（你以带有 sigmoid 激活的单元层结束模型），因此最好使用 binary_crossentropy 损失。它不是唯一可行的选择：例如，你可以使用 mean_squared_error。但当你处理

![](img/ab452ecf572a1f1372915be13bd8088f_125_0.png)

### 什么是激活函数，为什么需要它们？

没有像 relu（也称为非线性）这样的激活函数，Dense 层将由两个线性操作组成——点积和加法：

```
output = dot(input, W) + b
```

该层只能学习输入数据的线性变换（仿射变换）：该层的假设空间将是将输入数据转换到 16 维空间的所有可能线性变换的集合。这样的假设空间太受限，无法从多层表示中受益，因为深层线性层堆叠仍将实现一个线性操作：添加更多层不会扩展假设空间（如你在第 2 章中所见）。

为了获得一个更丰富、能从深层表示中受益的假设空间，你需要一个非线性，即激活函数。relu 是深度学习中最流行的激活函数，但还有许多其他候选者，它们都有着同样奇怪的名称：prelu、elu 等等。

处理输出概率的模型时。交叉熵是信息论领域的一个量度，用于衡量概率分布之间的距离，或在此例中，基实分布与你的预测之间的距离。

关于优化器的选择，我们将使用 rmsprop，它通常是几乎任何问题的不错默认选择。

以下是使用 rmsprop 优化器和 binary_crossentropy 损失函数配置模型的步骤。请注意，我们还将在训练期间监控准确率。

### 清单 4.5 编译模型

```python
model.compile(optimizer="rmsprop",
loss="binary_crossentropy",
metrics=["accuracy"])
```

## 4.1.4 验证你的方法

如你在第 3 章中所学，深度学习模型绝不应在训练数据上进行评估——使用验证集来监控模型在训练期间的准确率是标准做法。在此，我们将通过从原始训练数据中划分出 10,000 个样本来创建验证集。

### 清单 4.6 划分验证集

```python
x_val = x_train[:10000]
partial_x_train = x_train[10000:]
y_val = y_train[:10000]
partial_y_train = y_train[10000:]
```

我们现在将以 512 个样本的小批量训练模型 20 个 epoch（对训练数据中所有样本进行 20 次迭代）。同时，我们将监控我们划分出来的那 10,000 个样本上的损失和准确率。我们通过将验证数据作为 validation_data 参数传递来实现这一点。

### 清单 4.7 训练你的模型

```python
history = model.fit(partial_x_train,
partial_y_train,
epochs=20,
batch_size=512,
validation_data=(x_val, y_val))
```

在 CPU 上，每个 epoch 耗时不到 2 秒——训练在 20 秒内结束。每个 epoch 结束时都会有短暂的停顿，因为模型正在计算验证数据 10,000 个样本上的损失和准确率。

请注意，model.fit() 的调用将返回一个 History 对象，如你在第 3 章中所见。该对象有一个名为 history 的成员，它是一个包含训练期间发生的一切数据的字典。让我们来看看它：

```
>>> history_dict = history.history
>>> history_dict.keys()
[u"accuracy", u"loss", u"val_accuracy", u"val_loss"]
```

该字典包含四个条目：每个在训练和验证期间监控的指标对应一个条目。在接下来的两个清单中，让我们使用 Matplotlib 将训练损失和验证损失并排绘制（见图 4.4），以及训练准确率和验证准确率（见图 4.5）。请注意，由于模型随机初始化不同，你的结果可能会略有差异。

![](img/ab452ecf572a1f1372915be13bd8088f_127_0.png)

**图 4.4** 训练和验证损失

![](img/ab452ecf572a1f1372915be13bd8088f_127_1.png)

**图 4.5** 训练和验证准确率

### 清单 4.8 绘制训练和验证损失

```python
import matplotlib.pyplot as plt
history_dict = history.history
loss_values = history_dict["loss"]
val_loss_values = history_dict["val_loss"]
epochs = range(1, len(loss_values) + 1)
plt.plot(epochs, loss_values, "bo", label="Training loss")
plt.plot(epochs, val_loss_values, "b", label="Validation loss")
plt.title("Training and validation loss")
plt.xlabel("Epochs")
plt.ylabel("Loss")
plt.legend()
plt.show()
```

### 清单 4.9 绘制训练和验证准确率

```python
plt.clf()
acc = history_dict["accuracy"]
val_acc = history_dict["val_accuracy"]
plt.plot(epochs, acc, "bo", label="Training acc")
plt.plot(epochs, val_acc, "b", label="Validation acc")
plt.title("Training and validation accuracy")
plt.xlabel("Epochs")
plt.ylabel("Accuracy")
plt.legend()
plt.show()
```

如你所见，训练损失随每个 epoch 减少，训练准确率随每个 epoch 增加。运行梯度下降优化时，你会期待这一点——你试图最小化的量应随每次迭代而减少。但验证损失和准确率并非如此：它们似乎在第四个 epoch 达到峰值。这是我们之前警告过的一个示例：在训练数据上表现更好的模型，不一定在从未见过的数据上表现更好。准确地说，你看到的是过拟合：第四个 epoch 之后，你在训练数据上过度优化，最终学习到的表示特定于训练数据，无法推广到训练集之外的数据。

在这种情况下，为防止过拟合，你可以在四个 epoch 后停止训练。一般来说，你可以使用一系列技术来减轻过拟合，我们将在第 5 章中介绍。

让我们从头开始训练一个新模型四个 epoch，然后在测试数据上对其进行评估。

### 清单 4.10 从头开始重新训练模型

```python
model = keras.Sequential([
    layers.Dense(16, activation="relu"),
    layers.Dense(16, activation="relu"),
```
