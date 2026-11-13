

## 5.4.4 为模型添加正则化

正则化技术是一组最佳实践，它们会主动阻碍模型完美拟合训练数据的能力，目标是在验证期间使模型表现更好。这被称为“正则化”模型，因为它倾向于使模型更简单、更“规则”，曲线更平滑、更“通用”；因此它对训练集的特异性较低，更能通过更紧密地逼近数据的潜流形来泛化。

请记住，为模型添加正则化是一个过程，应始终由准确的评估程序指导。只有能够衡量泛化能力，才能实现泛化。

让我们回顾一些最常见的正则化技术，并在实践中将它们应用于改进第 4 章中的电影分类模型。

## 减小网络规模

你已经知道，模型过小不会过拟合。缓解过拟合最简单的方法是减小模型规模（模型中可学习参数的数量，由层数和每层单元数决定）。如果模型的记忆资源有限，它就无法简单地记忆训练数据；因此，为了最小化损失，它将不得不求助于学习具有预测能力的压缩表示，这正是我们感兴趣的表示类型。同时，请记住，应使用具有足够参数以避免欠拟合的模型：你的模型不应缺乏记忆资源。在 _容量过大_ 和 _容量不足_ 之间存在一个需要权衡的折中方案。

遗憾的是，没有神奇的公式来确定合适的层数或每层的合适大小。你必须评估一系列不同的架构（当然是在验证集上，而不是测试集上），以找到适合你数据的正确模型大小。寻找合适模型大小的一般工作流程是从相对较少的层和参数开始，然后增加层大小或添加新层，直到验证损失的收益开始递减。

让我们在电影评论分类模型上尝试这一点。下面的清单展示了我们的原始模型。

### 清单 5.10 原始模型

```
from tensorflow.keras.datasets import imdb
(train_data, train_labels), _ = imdb.load_data(num_words=10000)

def vectorize_sequences(sequences, dimension=10000):
    results = np.zeros((len(sequences), dimension))
    for i, sequence in enumerate(sequences):
        results[i, sequence] = 1.
    return results

train_data = vectorize_sequences(train_data)

model = keras.Sequential([
    layers.Dense(16, activation="relu"),
    layers.Dense(16, activation="relu"),
    layers.Dense(1, activation="sigmoid")
])
model.compile(optimizer="rmsprop",
    loss="binary_crossentropy",
    metrics=["accuracy"])
history_original = model.fit(train_data, train_labels,
    epochs=20, batch_size=512, validation_split=0.4)
```

现在，让我们尝试用这个更小的模型替换它。

### 清单 5.11 容量较低的模型版本

```
model = keras.Sequential([
    layers.Dense(4, activation="relu"),
    layers.Dense(4, activation="relu"),
    layers.Dense(1, activation="sigmoid")
])
model.compile(optimizer="rmsprop",
    loss="binary_crossentropy",
    metrics=["accuracy"])
history_smaller_model = model.fit(
    train_data, train_labels,
    epochs=20, batch_size=512, validation_split=0.4)
```

图 5.17 展示了原始模型和较小模型的验证损失对比。

![](img/ab452ecf572a1f1372915be13bd8088f_170_0.png)

图 5.17 IMDB 评论分类中原始模型与较小模型的对比

如你所见，较小模型开始过拟合的时间比参考模型更晚（六个 epoch 而非四个），一旦开始过拟合，其性能下降得更慢。

现在，让我们在基准中添加一个容量远大于问题所需的模型。尽管使用明显超参数化的模型是常见做法，但*记忆容量过大*确实是一种可能存在的情况。如果模型立即开始过拟合，且其验证损失曲线波动剧烈、方差高，则说明模型过大（不过，验证指标波动剧烈也可能是使用不可靠验证过程的症状，例如验证集划分过小）。

### 清单 5.12 容量较高的模型版本

```
model = keras.Sequential([
    layers.Dense(512, activation="relu"),
    layers.Dense(512, activation="relu"),
    layers.Dense(1, activation="sigmoid")
])
model.compile(optimizer="rmsprop",
              loss="binary_crossentropy",
              metrics=["accuracy"])
history_larger_model = model.fit(
    train_data, train_labels,
    epochs=20, batch_size=512, validation_split=0.4)
```

图 5.18 展示了较大模型与参考模型相比的表现。

![](img/ab452ecf572a1f1372915be13bd8088f_171_0.png)

图 5.18 IMDB 评论分类中原始模型与大得多的模型的对比

较大模型几乎立即开始过拟合，仅经过一个 epoch，并且过拟合程度要严重得多。其验证损失也更加嘈杂。它能非常快地将训练损失降至接近零。模型容量越大，它就能越快地对训练数据建模（导致训练损失较低），但也越容易过拟合（导致训练损失与验证损失之间存在较大差异）。

## 添加权重正则化

你可能熟悉*奥卡姆剃刀*原理：对于某事物的两种解释，最可能正确的解释是最简单的那个——即假设更少的那个。这一思想也适用于神经网络学习的模型：给定一些训练数据和网络架构，多组权重值（多个*模型*）都可以解释数据。简单模型比复杂模型更不容易过拟合。

在这个语境下，*简单模型*是指参数值分布熵较小（或参数较少，如前一节所示）的模型。因此，缓解过拟合的一种常见方法是通过强制权重仅取较小值来限制模型的复杂度，这使得权重值的分布更加*规则*。这称为*权重正则化*，实现方法是向模型的损失函数中添加与权重值较大相关联的代价。这种代价有两种形式：

- *L1 正则化*——添加的代价与权重系数的*绝对值*（权重的*L1 范数*）成正比。
- *L2 正则化*——添加的代价与权重系数值的*平方*（权重的*L2 范数*）成正比。在神经网络语境下，L2 正则化也称为*权重衰减*。不要被不同的名称混淆：权重衰减在数学上等同于 L2 正则化。

在 Keras 中，通过将*权重正则化器实例*作为关键字参数传递给层来添加权重正则化。让我们向最初的电影评论分类模型添加 L2 权重正则化。

### 清单 5.13 向模型添加 L2 权重正则化

```
from tensorflow.keras import regularizers
model = keras.Sequential([
    layers.Dense(16,
    kernel_regularizer=regularizers.l2(0.002),
    activation="relu"),
    layers.Dense(16,
    kernel_regularizer=regularizers.l2(0.002),
    activation="relu"),
    layers.Dense(1, activation="sigmoid")
])
model.compile(optimizer="rmsprop",
loss="binary_crossentropy",
metrics=["accuracy"])
history_l2_reg = model.fit(
    train_data, train_labels,
    epochs=20, batch_size=512, validation_split=0.4)
```

在前面的清单中，l2(0.002) 表示该层权重矩阵中的每个系数会向模型总损失添加 0.002 * weight_coefficient_value ** 2。请注意，由于此惩罚仅在训练期间添加，因此该模型在训练时的损失将远高于测试时。

图 5.19 展示了 L2 正则化惩罚的影响。如你所见，带有 L2 正则化的模型比参考模型更能抵抗过拟合，尽管两个模型具有相同数量的参数。

![](img/ab452ecf572a1f1372915be13bd8088f_173_0.png)

图 5.19 L2 权重正则化对验证损失的影响

作为 L2 正则化的替代方案，你可以使用以下 Keras 权重正则化器之一。

### 清单 5.14 Keras 中可用的不同权重正则化器

```
from tensorflow.keras import regularizers
regularizers.l1(0.001)  # L1 regularization
regularizers.l1_l2(l1=0.001, l2=0.001)  # Simultaneous L1 and L2 regularization
```

请注意，权重正则化更多地用于较小的深度学习模型。大型深度学习模型往往明显超参数化，以至于对权重值施加约束对模型容量和泛化能力影响不大。在这些情况下，更偏好的方法是另一种正则化技术：丢弃法。

