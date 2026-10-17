
```python
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

清单14.14：双圆形问题上过拟合MLP的示例。

运行示例会报告模型在训练集和测试集上的性能。

**注意**：由于学习算法的随机性，您的具体结果可能会有所不同。请考虑多次运行示例并比较平均性能。

我们可以看到，模型在训练数据集上的性能优于测试数据集，这可能是过拟合的一个迹象。

```text
Train: 1.000, Test: 0.757
```

清单14.15：双圆形问题上过拟合MLP的示例输出。

生成了一个图形，显示模型在训练集和测试集上的损失和准确率的线图。我们可以清楚地看到过拟合模型的典型形态：测试准确率先上升到一个点，然后开始下降。损失的效果更为明显，随着训练的继续，测试集损失大幅增加。

![训练期间训练集和测试集准确率的线图，显示过拟合。](img/8b574b0ce3be1eda9e1c02c72f9c8a21_317_0.png)

图14.2：训练期间训练集和测试集准确率的线图，显示过拟合。

## 14.3.3 带激活正则化的过拟合MLP

我们可以更新示例以使用激活正则化。有几种不同的正则化方法可供选择，但使用最常见的L1向量范数可能是一个好主意。这种正则化能够鼓励稀疏表示（大量为零），而修正线性激活函数允许真正的零值，因此支持这种正则化。我们可以通过使用Keras中的`keras.regularizers.l1`类来实现。

我们将配置该层使用线性激活函数，以便对原始输出进行正则化，然后在该层正则化输出之后添加一个relu激活层。我们将正则化超参数设置为1E-4或0.0001，这是通过一点试错得到的。

```python
model.add(Dense(500, input_dim=2, activation='linear', activity_regularizer=l1(0.0001)))
model.add(Activation('relu'))
```

清单14.16：在激活之前添加激活正则化的示例。

带有L1范数约束的完整更新示例如下：

```python
# mlp overfit on the two circles dataset with activation regularization before activation
from sklearn.datasets import make_circles
from keras.layers import Dense
from keras.models import Sequential
from keras.regularizers import l1
from keras.layers import Activation
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_circles(n_samples=100, noise=0.1, random_state=1)
# split into train and test
n_train = 30
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(500, input_dim=2, activation='linear', activity_regularizer=l1(0.0001)))
model.add(Activation('relu'))
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

清单14.17：在激活之前使用激活正则化的MLP在双圆形问题上的示例。

运行示例会报告模型在训练集和测试集上的性能。

**注意**：由于学习算法的随机性，您的具体结果可能会有所不同。请考虑多次运行示例并比较平均性能。

在这种情况下，我们可以看到激活正则化导致训练数据集上的准确率从100%略微下降到96%，而测试集上的准确率从78%上升到81%。

```text
Train: 0.967, Test: 0.814
```

清单14.18：在激活之前使用激活正则化的MLP在双圆形问题上的示例输出。

查看训练和测试准确率的线图，我们可以发现模型似乎不再像之前那样强烈地过拟合训练数据集。模型在训练集和测试集上的准确率都持续上升到平稳状态。

```python
model.add(Dense(500, input_dim=2, activation='relu', activity_regularizer=l1(0.0001)))
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

清单14.20：在激活之后使用激活正则化的MLP在双圆形问题上的示例。

运行示例会报告模型在训练集和测试集上的性能。

**注意**：由于学习算法的随机性，您的具体结果可能会有所不同。请考虑多次运行示例并比较平均性能。

在这种情况下，我们可以看到，至少在这个问题上，对于这个模型，激活函数之后的激活正则化并没有改善泛化误差；事实上，它使情况变得更糟。

```text
Train: 1.000, Test: 0.757
```

清单14.21：在激活之后使用激活正则化的MLP在双圆形问题上的示例输出。

查看训练和测试准确率的线图，我们可以看到模型确实仍然显示出过拟合训练数据集的迹象。

![使用激活正则化训练时训练集和测试集准确率的线图，仍然过拟合。](img/8b574b0ce3be1eda9e1c02c72f9c8a21_321_0.png)

图14.4：使用激活正则化训练时训练集和测试集准确率的线图，仍然过拟合。

这表明，在您自己的数据集上实现激活正则化时，也许值得同时尝试这两种方法，以确认您能充分利用该方法。

## 14.4 扩展

本节列出了一些您可能希望探索的扩展本教程的想法。

- **报告激活均值**。更新示例，计算正则化层的平均激活值，并确认激活确实变得更稀疏。
- **网格搜索**。更新示例，对正则化超参数的不同值进行网格搜索。
- **替代范数**。更新示例，评估L2或L1和L2向量范数对隐藏层输出进行正则化的效果。
- **重复评估**。更新示例，多次拟合和评估模型，并报告模型性能的均值和标准差。

如果您探索了其中任何扩展，我很乐意知道。

## 14.5 扩展阅读

本节提供了更多关于该主题的资源，如果你想深入了解。

### 14.5.1 书籍

- 第 7.10 节 稀疏表示，*深度学习*，2016. https://amzn.to/2NJW3gE

### 14.5.2 论文

- *深度稀疏整流神经网络*, 2011. http://proceedings.mlr.press/v15/glorot11a.html
- *用于深度信念网络的稀疏特征学习*, 2007. http://papers.nips.cc/paper/3363-sparse-feature-learning-for-deep-belief-networks
- *无监督不变特征层次学习及其在目标识别中的应用*, 2007. https://ieeexplore.ieee.org/document/4270182/
- *高效稀疏编码算法*, 2007. https://dl.acm.org/citation.cfm?id=2976557
- *衡量深度网络中的不变性*, 2009. https://papers.nips.cc/paper/3790-measuring-invariances-in-deep-networks
- *视觉区 V2 的稀疏深度信念网络模型*, 2007. https://papers.nips.cc/paper/3313-sparse-deep-belief-net-model-for-visual-area-v2
- *重新审视语言 RNN 的激活正则化*, 2017. https://arxiv.org/abs/1708.01009
- *监督学习中的稀疏活动和稀疏连接*, 2013. http://jmlr.org/papers/v14/thom13a.html

### 14.5.3 API

- Keras 正则化器 API. https://keras.io/regularizers/
- Keras 核心层 API. https://keras.io/layers/core/
- Keras 卷积层 API. https://keras.io/layers/convolutional/
- Keras 循环层 API. https://keras.io/layers/recurrent/
- `sklearn.datasets.make_circles` API. http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_circles.html

### 14.5.4 文章

- 稀疏编码，Scholarpedia. http://www.scholarpedia.org/article/Sparse_coding
- 稀疏自编码器，CS294A 讲义. https://web.stanford.edu/class/cs294a/sparseAutoencoder.pdf

## 14.6 摘要

在本教程中，你了解了激活正则化作为一种提高学习特征泛化能力的技术。具体来说，你学习了：

- 神经网络从数据和模型中学习特征，例如自编码器和编码器-解码器模型，并明确寻求有效的学习表示。
- 与权重类似，学习特征中的大值，例如大激活，可能表明模型过拟合。
- 在损失函数中添加按激活幅度比例惩罚模型的惩罚项，可能导致更稳健和泛化更好的学习特征。

### 14.6.1 下一步

在下一个教程中，你将了解如何更新模型并添加约束，以确保训练过程中模型权重保持较小。

## 第 15 章

## 使用权重约束强制权重变小

权重正则化方法如权重衰减在训练神经网络时向损失函数引入惩罚，以鼓励网络使用较小的权重。神经网络中较小的权重可以使模型更稳定，不太可能过拟合训练数据集，从而在对新数据进行预测时表现更好。与权重正则化不同，权重约束是一个触发器，检查权重的大小或幅度并对其进行缩放，使其全部低于预定义的阈值。约束强制权重变小，可以替代权重衰减使用，并与更激进的网络配置（如非常大的学习率）结合使用。在本教程中，你将了解权重约束正则化的使用，作为减少深度神经网络过拟合的权重惩罚的替代方案。

阅读本教程后，你将知道：

- 权重惩罚鼓励但不要求神经网络具有较小的权重。
- 权重约束，例如 L2 范数和最大范数，可用于在训练期间强制神经网络具有较小的权重。
- 权重约束在使用与其他正则化方法如 dropout 结合时可以改善泛化能力。

开始吧。

### 15.1 权重约束

在本节中，你将发现具有大权重的神经网络的问题，一种可用于强制开发具有小权重的模型的技术，称为权重约束，以及在自己的项目中使用该技术的技巧。

#### 15.1.1 大权重惩罚的替代方案

神经网络中的大权重是过拟合的迹象。具有大权重的网络很可能学习了训练数据中的统计噪声。这导致模型不稳定，对输入变量的变化非常敏感。进而，过拟合的网络在对新的未见数据进行预测时表现不佳。解决该问题的一种流行且有效的方法是更新训练期间优化的损失函数，以考虑权重的大小。
