
# plot loss learning curves
```
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

清单 16.17：绘制 MLP 模型性能的示例。

我们可以将所有这些部分联系起来；完整的示例如下所示。

```
# mlp overfit on the two circles dataset
from sklearn.datasets import make_circles
from keras.layers import Dense
from keras.models import Sequential
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_circles(n_samples=100, noise=0.1, random_state=1)
# split into train and test
n_train = 30
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(500, input_dim=2, activation='relu'))
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

列表 16.18: 对两个圆问题拟合 MLP 的示例。

运行示例会报告模型在训练集和测试集上的性能。我们可以看到模型在训练数据集上的性能优于测试数据集，这是过拟合的一个可能迹象。

注意：由于学习算法的随机性，你的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

```
Train: 1.000, Test: 0.771
```

列表 16.19: 对两个圆问题拟合 MLP 的示例输出。

创建了一幅图，显示模型在训练集和测试集上的性能线图。我们可以看到过拟合模型的预期形状，其中测试损失和准确率会改善到某一点，然后随着训练的继续开始变差。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_352_0.png)

图 16.2：训练过程中训练集和测试集准确率的线图，显示过拟合。

## 16.3.3 使用 Dropout 正则化的 MLP

我们可以更新示例以使用 dropout 正则化。我们只需在隐藏层和输出层之间插入一个新的 `Dropout` 层即可。在此情况下，我们将指定 dropout 率（将隐藏层输出设为零的概率）为 40% 或 `0.4`。

```
# define model
model = Sequential()
model.add(Dense(500, input_dim=2, activation='relu'))
model.add(Dropout(0.4))
model.add(Dense(1, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
```

列表 16.20: 带有 dropout 的 MLP 示例。

隐藏层后添加 dropout 的完整更新示例如下所示：

```python
# mlp with dropout on the two circles dataset
from sklearn.datasets import make_circles
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import Dropout
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_circles(n_samples=100, noise=0.1, random_state=1)
# split into train and test
n_train = 30
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(500, input_dim=2, activation='relu'))
model.add(Dropout(0.4))
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

列表 16.21: 对两个圆问题拟合带有 dropout 的 MLP 的示例。

运行示例会报告模型在训练集和测试集上的性能。

注意：由于学习算法的随机性，你的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

在这种特定情况下，我们可以看到 dropout 导致训练数据集上的准确率略有下降，从 100% 下降到 96%，而测试集上的准确率有所提升，从 77% 上升到 81%。

```
Train: 0.967, Test: 0.814
```

列表 16.22: 对两个圆问题拟合带有 dropout 的 MLP 的示例输出。

回顾训练过程中训练集和测试集准确率的线图，我们可以看到模型似乎不再过拟合训练数据集。训练集和测试集上的模型准确率都继续增加到一个平台期，尽管由于训练过程中使用了 dropout，存在大量噪声。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_354_0.png)

图 16.3：使用 Dropout 正则化训练时训练集和测试集准确率的线图。

## 16.4 扩展

本节列出了一些扩展本教程的想法，你可能希望探索。

- **输入 Dropout**。更新示例以对输入变量使用 dropout 并比较结果。
- **权重约束**。更新示例以向隐藏层添加 max-norm 权重约束并比较结果。
- **重复评估**。更新示例以重复评估过拟合和 dropout 模型，并汇总和比较平均结果。
- **网格搜索率**。开发 dropout 概率的网格搜索，并报告 dropout 率与测试集准确率之间的关系。

如果你探索其中任何一个扩展，我很想知道。

## 16.5 进一步阅读

如果你想深入了解，本节提供了有关该主题的更多资源。

### 16.5.1 书籍

- 第 7.12 节：Dropout，*深度学习*，2016。
  https://amzn.to/2NJW3gE
- 第 4.4.3 节：添加 dropout，*使用 Python 的深度学习*，2017。
  https://amzn.to/2wVqZDq

### 16.5.2 论文

- *通过防止特征检测器的协同适应来改进神经网络*，2012。
  https://arxiv.org/abs/1207.0580
- *Dropout：防止神经网络过拟合的一种简单方法*，2014。
  http://jmlr.org/papers/v15/srivastava14a.html
- *使用整流线性单元和 dropout 改进 LVCSR 的深度神经网络*，2013。
  https://ieeexplore.ieee.org/document/6639346/
- *Dropout 训练作为自适应正则化*，2013。
  https://arxiv.org/abs/1307.1493
- *使用卷积网络进行高效目标定位*，2015。
  https://arxiv.org/abs/1411.4280
- *在循环神经网络中对 Dropout 的理论基础应用*，2016。
  https://arxiv.org/abs/1512.05287

### 16.5.3 API

- Keras 正则化器 API。
  https://keras.io/regularizers/
- Keras 核心层 API。
  https://keras.io/layers/core/
- Keras 卷积层 API。
  https://keras.io/layers/convolutional/
- Keras 循环层 API。
  https://keras.io/layers/recurrent/
- `sklearn.datasets.make_circles` API。
  http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_circles.html

### 16.5.4 文章

- Dropout（神经网络），维基百科。
  https://en.wikipedia.org/wiki/Dropout_(neural_networks)
- 正则化，CS231n 卷积神经网络视觉识别。
  http://cs231n.github.io/neural-networks-2/#reg
- ‘Dropout’是如何构想的？有没有‘顿悟’时刻？
  https://www.reddit.com/r/MachineLearning/comments/4w6tsv/ama_we_are_the_google_brain_team_wed_love_to/d64yyas

## 16.6 摘要

在本教程中，你了解了使用 dropout 正则化来减少过拟合并提高深度神经网络泛化能力。具体来说，你学习了：

- 神经网络中的大权重是网络更复杂且已过拟合训练数据的迹象。
- 以概率方式丢弃网络中的节点是一种简单而有效的正则化方法。
- 使用 dropout 时，建议使用更大的网络、更多的训练轮次以及使用权重约束。

### 16.6.1 下一步

在下一个教程中，你将了解如何通过添加统计噪声来提高神经网络模型的鲁棒性。

## 第17章

## 用噪声提升鲁棒性

使用小数据集训练神经网络会导致网络记住所有训练样本，进而在留出数据集上表现不佳。小数据集也可能给神经网络带来更难学习的映射问题，因为高维输入空间中的点采样稀疏或不完整。一种使输入空间更平滑、更易于学习的方法是在训练期间向输入添加噪声。在本教程中，你将发现，在训练期间向神经网络添加噪声可以提高网络的鲁棒性，从而获得更好的泛化能力和更快的学习速度。阅读本教程后，你将了解：

- 小数据集会让神经网络的学习变得困难，并且样本可能被记住。
- 在训练期间添加噪声可以使训练过程更加鲁棒，并减少泛化误差。
- 传统上，噪声被添加到输入中，但也可以添加到权重、梯度，甚至激活函数中。

让我们开始吧。

### 17.1 噪声正则化

在本节中，你将了解大网络权重的脆弱性，以及添加统计噪声如何产生正则化效果，并了解在你自己的神经网络模型中添加噪声时可能会有帮助的一些技巧。

### 17.1.1 小训练数据集的挑战

小数据集在训练大型神经网络时会带来问题。第一个问题是，网络可能会有效地记住训练数据集。模型不是学习从输入到输出的通用映射，而可能学习的是具体输入样本及其对应的输出。这将导致模型在训练数据集上表现良好，而在新数据（如留出数据集）上表现不佳。第二个问题是，小数据集提供了较少的机会来描述输入空间的结构及其与输出的关系。更多的训练数据提供了更丰富的问题描述，便于模型学习。数据点较少意味着，输入空间可能不是平滑的，而是可能代表一种突兀且不连贯的结构，从而可能导致一个困难甚至不可学习的映射函数。获取更多数据并不总是可行的。此外，获得更多数据也可能无法解决这些问题。

### 17.1.2 训练期间添加随机噪声

改善泛化误差和映射问题结构的一种方法是添加随机噪声。

许多研究 [...] 指出，向训练数据中添加少量输入噪声（抖动）通常有助于泛化和容错。

> ——第273页，*《神经锻造：前馈人工神经网络中的监督学习》*，1999年。

乍一听，这像是让学习变得更加困难的一种方法。这是一个反直觉的提高性能的建议，因为人们会预期噪声会降低模型在训练期间的表现。

启发式地看，我们可能预期噪声会“抹匀”每个数据点，使网络难以精确拟合各个数据点，从而减少过拟合。实际上，已有实践证明，带噪声训练确实可以改善网络的泛化能力。

> ——第347页，*《用于模式识别的神经网络》*，1995年。

在训练神经网络模型期间添加噪声具有正则化效果，并由此提高模型的鲁棒性。已经证明，它对损失函数的影响类似于添加惩罚项，就像权重正则化方法一样。

众所周知，在训练期间向神经网络输入数据添加噪声，在某些情况下可以显著提高泛化性能。以前的工作表明，这种带噪声训练等价于一种正则化形式，即在误差函数中添加一个额外项。

> ——*《带噪声训练等价于吉洪诺夫正则化》*，2008年。

实际上，添加噪声扩大了训练数据集的规模。每次训练样本暴露给模型时，都会向输入变量添加随机噪声，使它们每次暴露给模型时都不同。这样，向输入样本添加噪声是一种简单的数据增强形式。

向神经网络输入注入噪声也可以看作一种数据增强形式。

——第241页，《深度学习》，2016年。

添加噪声意味着网络不太可能记住训练样本，因为它们一直在变化，从而产生更小的网络权重和更鲁棒的网络，泛化误差更低。这种噪声就好像从已知样本附近的领域中不断抽取新样本，从而使输入空间的结构变得平滑。这种平滑可能意味着网络更容易学习映射函数，从而实现更好、更快的学习。

> ...输入噪声和权重噪声分别促使神经网络输出成为输入或其权重的平滑函数。

——反向传播训练期间添加噪声对泛化性能的影响，1996年。

### 17.1.3 如何以及在哪里添加噪声
