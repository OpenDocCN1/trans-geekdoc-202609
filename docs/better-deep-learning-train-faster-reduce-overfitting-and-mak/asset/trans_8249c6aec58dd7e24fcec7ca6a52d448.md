
### Listing 15.12: 双月问题上过拟合 MLP 的示例。

运行示例会报告模型在训练集和测试集上的性能。我们可以看到模型在训练集上的表现优于测试集，这是过拟合的可能迹象之一。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。建议多次运行示例并比较平均性能。

```
Train: 1.000, Test: 0.914
```

### Listing 15.13: 双月问题上过拟合 MLP 的示例输出。

创建了一幅图，显示模型在训练集和测试集上的损失和准确率的线图。我们可以看到过拟合模型的预期形状，其中测试准确率增加到某一点后开始再次下降。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_333_0.png)

### Figure 15.2: 训练过程中训练集和测试集准确率的线图显示过拟合。

## 15.3.3 带权重约束的过拟合 MLP

我们可以更新示例以使用权重约束。有几种不同的权重约束可供选择。对于此模型，一个简单而良好的约束就是简单地归一化权重，使其范数等于 1.0。该约束的效果是强制所有传入权重保持较小。我们可以通过在 Keras 中使用 `unit_norm` 来实现。可以在第一个隐藏层中按如下方式添加此约束：

```
model.add(Dense(500, input_dim=2, activation='relu', kernel_constraint=unit_norm()))
```

### Listing 15.14: 添加单位范数权重约束的示例。

我们也可以通过使用 `min_max_norm` 并将最小值和最大值都设置为 1.0 来实现相同的结果，例如：

```
model.add(Dense(500, input_dim=2, activation='relu',
    kernel_constraint=min_max_norm(min_value=1.0, max_value=1.0)))
```

### Listing 15.15: 添加最小-最大范数权重约束的示例。

我们无法使用最大范数约束实现相同的结果，因为它允许范数小于或等于指定限制；例如：

```
model.add(Dense(500, input_dim=2, activation='relu', kernel_constraint=max_norm(1.0)))
```

### Listing 15.16: 添加最大范数权重约束的示例。

带有单位范数约束的完整更新示例如下所示：

```
# mlp overfit on the moons dataset with a unit norm constraint
from sklearn.datasets import make_moons
from keras.layers import Dense
from keras.models import Sequential
from keras.constraints import unit_norm
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_moons(n_samples=100, noise=0.2, random_state=1)
# split into train and test
n_train = 30
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(500, input_dim=2, activation='relu', kernel_constraint=unit_norm()))
model.add(Dense(1, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=4000, verbose=0)
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

### Listing 15.17: 双月问题上带权重约束的 MLP 示例。

运行示例会报告模型在训练集和测试集上的性能。我们可以看到，确实，对权重大小的严格约束提高了模型在保留集上的性能，而不会影响训练集上的性能。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。建议多次运行示例并比较平均性能。

```
Train: 1.000, Test: 0.943
```

### Listing 15.18: 双月问题上带权重约束的 MLP 的示例输出。

查看训练集和测试集损失与准确率的线图，我们可以看到模型似乎不再对训练数据集过拟合。模型在训练集和测试集上的准确率持续提高直至达到平台期。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_336_0.png)

### Figure 15.3: 训练过程中带权重约束的训练集和测试集准确率线图。

## 15.4 扩展

本节列出了一些您可以探索的扩展教程的想法。

- **报告权重范数。** 更新示例以计算单位权重的大小，并证明约束确实使大小变小。
- **约束输出层。** 更新示例以向模型的输出层添加约束并比较结果。
- **约束偏置。** 更新示例以向偏置权重添加约束并比较结果。
- **重复评估。** 更新示例多次拟合和评估模型，并报告模型性能的均值和标准差。

如果您探索了这些扩展中的任何一个，我很想知道。

## 15.5 进一步阅读

如果您想深入了解，本节提供了更多相关资源。

### 15.5.1 书籍

- 第 7.2 节：作为约束优化的范数惩罚，*深度学习*，2016. https://amzn.to/2NJW3gE

### 15.5.2 论文

- *Dropout：防止神经网络过拟合的简单方法*，2014. http://jmlr.org/papers/v15/srivastava14a.html
- *秩、迹范数和最大范数*，2005. https://link.springer.com/chapter/10.1007/11503415_37
- *通过防止特征检测器的协同适应来改进神经网络*，2012. https://arxiv.org/abs/1207.0580

### 15.5.3 API

- Keras 约束 API。 https://keras.io/constraints/
- Keras constraints.py。 https://github.com/keras-team/keras/blob/master/keras/constraints.py
- Keras 核心层 API。 https://keras.io/layers/core/
- Keras 卷积层 API。 https://keras.io/layers/convolutional/
- Keras 循环层 API。 https://keras.io/layers/recurrent/
- sklearn.datasets.make_moons API。 http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_moons.html

### 15.5.4 文章

- 范数（数学），维基百科。 https://en.wikipedia.org/wiki/Norm_(mathematics)
- 正则化，神经网络第 2 部分：设置数据和损失，CS231n 卷积神经网络视觉识别。 http://cs231n.github.io/neural-networks-2/#reg

## 15.6 摘要

在本教程中，您了解了权重约束正则化的使用，作为权重惩罚的替代方法，以减少深度神经网络中的过拟合。具体来说，您学习了：

- 权重惩罚鼓励但不要求神经网络具有较小的权重。
- 诸如 L2 范数和最大范数之类的权重约束可用于在训练期间强制神经网络具有较小的权重。
- 权重约束在使用其他正则化方法（如 dropout）结合时可以改善泛化能力。

### 15.6.1 下一步

在下一个教程中，您将了解 dropout 正则化，它可以解耦神经网络模型中的层。

## 第 16 章：使用 Dropout 解耦层

深度学习神经网络很可能在示例较少的训练数据集上迅速过拟合。具有不同模型配置的神经网络集成已知可以减少过拟合，但需要训练和维护多个模型的额外计算开销。单个模型可以通过在训练期间随机丢弃节点来模拟拥有大量不同的网络架构。这称为 dropout，提供了一种计算成本非常低且非常有效的正则化方法，可减少各种深度神经网络中的过拟合和泛化误差。在本教程中，您将了解 dropout 正则化的使用，以减少过拟合并提高深度神经网络的泛化能力。阅读本教程后，您将知道：

- 神经网络中的大权重是网络更复杂且已对训练数据过拟合的迹象。
- 以概率方式丢弃网络中的节点是一种简单而有效的正则化方法。
- 使用 dropout 时建议使用更大的网络、更多的训练 epoch 以及使用权重约束。

开始吧。

### 16.1 Dropout

在本节中，您将发现可以在一个名为 dropout 的单一模型中模拟大型神经网络模型集成的发展，了解如何使用它来减少过拟合，以及在自己的项目中使用此技术的提示。

### 16.1.1 过拟合问题

在相对较小的数据集上训练的大型神经网络可能会过拟合训练数据。这会导致模型学习训练数据中的统计噪声，从而导致模型在新数据（例如测试数据集）上评估时性能不佳。泛化误差因过拟合而增加。减少过拟合的一种方法是拟合同一数据集上的所有可能的神经网络，并对每个模型的预测进行平均。这就是
