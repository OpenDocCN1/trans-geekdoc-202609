
Train: 0.588, Test: 0.552

清单 7.21：评估两圆问题中更深的基于 tanh 的 MLP 的示例输出。

模型在训练过程中在训练集和测试集上的准确率线图讲述了类似的故事。我们可以看到性能很差，并且随着训练的进行实际上变得更糟。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_193_0.png)

图 7.4：两圆问题中深度 MLP 在训练轮次中训练集和测试集准确率的线图。

## 7.3.4 使用 ReLU 的更深 MLP 模型

修正线性激活函数已取代双曲正切激活函数，成为开发多层感知器网络以及其他

像 CNN 这样的网络类型。这是因为激活函数看起来并表现得像线性函数，使得训练更容易且不太可能饱和，但实际上它是非线性函数，会将负输入强制为值 0。它被认为是在训练更深模型时解决梯度消失问题的一种可能方法。在使用修正线性激活函数（简称 ReLU）时，使用 He 权重初始化方案是良好的实践。我们可以使用 ReLU 和 He 初始化定义具有五个隐藏层的 MLP，如下所示。

```
# define model

model = Sequential()

model.add(Dense(5, input_dim=2, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(1, activation='sigmoid'))
```

Listing 7.22: 定义一个更深的基于 ReLU 的 MLP 的示例。

将这些结合起来，完整的代码示例如下所示。

```
# deeper mlp with relu for the two circles classification problem (5 hidden layers)

from sklearn.datasets import make_circles

from sklearn.preprocessing import MinMaxScaler

from keras.layers import Dense

from keras.models import Sequential

from keras.optimizers import SGD

from matplotlib import pyplot

# generate 2d classification dataset

X, y = make_circles(n_samples=1000, noise=0.1, random_state=1)

scaler = MinMaxScaler(feature_range=(-1, 1))

X = scaler.fit_transform(X)

# split into train and test

n_train = 500

trainX, testX = X[:n_train, :], X[n_train:, :]

trainy, testy = y[:n_train], y[n_train:]

# define model

model = Sequential()

model.add(Dense(5, input_dim=2, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(1, activation='sigmoid'))

# compile model

opt = SGD(lr=0.01, momentum=0.9)

model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])

# fit model

history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=500, verbose=0)

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

Listing 7.23: 评估用于双圆分类问题的更深 ReLU 基于 MLP 的示例。

运行示例会打印模型在训练集和测试集上的性能。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

在这种情况下，我们可以看到这一小改动使模型能够学习该问题，在两个数据集上均实现了约 84% 的准确率，优于使用 tanh 激活函数的单层模型。

```
Train: 0.842, Test: 0.846
```

Listing 7.24: 评估用于双圆问题的更深 ReLU 基于 MLP 的示例输出。

还创建了模型在训练 epoch 过程中训练集和测试集准确率的线图。该图显示了与迄今为止所见相当不同的动态。模型似乎能快速学习该问题，在约 100 个 epoch 内收敛到解决方案。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_196_0.png)

Figure 7.5: 双圆问题中具有 ReLU 的深度 MLP 在训练 epoch 过程中训练集和测试集准确率的线图。

使用 ReLU 激活函数使我们能够为此简单问题拟合一个更深的模型，但这种能力并非无限。例如，增加层数会导致学习变慢，在约 20 层时模型不再能够学习该问题，至少在所选配置下如此。例如，下面是具有 15 个隐藏层的相同模型的训练和测试准确率线图，显示它仍然能够学习该问题（至少有时）。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_197_0.png)

Figure 7.6: 具有 15 个隐藏层的 ReLU 深度 MLP 在训练 epoch 过程中训练集和测试集准确率的线图。

下面是具有 20 层的相同模型在 epoch 过程中训练和测试准确率的线图，显示该配置不再能够学习该问题（至少有时）。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_198_0.png)

Figure 7.7: 具有 20 个隐藏层的 ReLU 深度 MLP 在训练 epoch 过程中训练集和测试集准确率的线图。

尽管使用 ReLU 是有效的，但我们不能确信 tanh 函数的失败是因为梯度消失，而 ReLU 的成功是因为它克服了这个问题。

## 7.4 扩展

本节列出了一些扩展本教程的想法，您可能希望探索。

- **权重初始化**。将使用 tanh 激活的深度 MLP 更新为使用 Xavier 均匀权重初始化并报告结果。
- **学习算法**。将使用 tanh 激活的深度 MLP 更新为使用 Adam 等自适应学习算法并报告结果。
- **权重变化**。更新 tanh 和 relu 示例以记录并绘制每个 epoch 模型权重的 L1 向量范数，作为训练期间各层变化程度的代理指标并比较结果。
- **研究模型深度**。使用具有 tanh 激活的 MLP 创建实验，并报告随着隐藏层数从 1 增加到 10 时模型的性能。
- **增加宽度**。将具有 tanh 激活的 MLP 的隐藏层中的节点数从 5 增加到 25，并报告随着层数从 1 增加到 10 时的性能。

如果您探索其中任何一个扩展，我很乐意知道。

## 7.5 进一步阅读

如果您想深入了解，本节提供了该主题的更多资源。

### 7.5.1 书籍

- 第 6.3.1 节：修正线性单元及其泛化，*深度学习*，2016。
  https://amzn.to/2QHVwmW

### 7.5.2 论文

- *什么是用于对象识别的最佳多阶段架构？*，2009
  https://ieeexplore.ieee.org/document/5459469
- *修正线性单元改进受限玻尔兹曼机*，2010。
  https://dl.acm.org/citation.cfm?id=3104425
- *深度稀疏整流神经网络*，2011。
  http://proceedings.mlr.press/v15/glorot11a
- *整流非线性改进神经网络声学模型*，2013。
  http://ai.stanford.edu/~amaas/papers/relu_hybrid_icml2013_final.pdf
- *理解训练深度前馈神经网络的困难*，2010。
  http://proceedings.mlr.press/v9/glorot10a.html
- *深入探究整流器：超越 ImageNet 分类的人类水平性能*，2015。
  https://arxiv.org/abs/1502.01852
- *Maxout 网络*，2013。
  https://arxiv.org/abs/1302.4389
- *用于训练非常深的前馈网络的随机游走初始化*，2014。
  https://arxiv.org/abs/1412.6558
- *循环网络中的梯度流：学习长期依赖的困难*，2001。
  http://www.iro.umontreal.ca/~lisa/publications2/index.php/publications/show/55

## 第8章
### 使用梯度裁剪修复梯度爆炸

训练神经网络可能会变得不稳定，这取决于误差函数、学习率的选择，甚至目标变量的尺度。训练过程中权重的大幅更新可能导致数值溢出或下溢，通常被称为梯度爆炸。梯度爆炸问题在循环神经网络中更为常见，例如 LSTM，因为在数百个输入时间步展开时梯度会累积。解决梯度爆炸问题的一种常见且相对简单的方法是在将误差的导数向后传播并用于更新权重之前对其进行更改。两种方法包括根据选定的向量范数重新缩放梯度以及裁剪超出首选范围的梯度值。这些方法合在一起被称为梯度裁剪。在本教程中，您将了解梯度爆炸问题以及如何使用梯度裁剪改善神经网络训练稳定性。完成本教程后，您将了解：

- 训练神经网络可能变得不稳定，导致通常被称为梯度爆炸的数值溢出或下溢。
- 通过按向量范数缩放误差梯度或将梯度值裁剪到一定范围，可以使训练过程稳定。
- 如何使用梯度裁剪方法更新具有梯度爆炸问题的回归预测建模问题的 MLP 模型，以实现稳定的训练过程。

让我们开始。

神经网络使用随机梯度下降优化算法进行训练。这首先需要估计一个或多个训练示例上的损失，然后计算损失的导数，该导数通过网络向后传播以更新权重。权重使用由学习率控制的反向传播误差的一部分进行更新。权重更新可能大到导致权重溢出或下溢其数值精度。实际上，当权重溢出或下溢时，权重可能取 NaN（非数字）或 Inf（无穷大）的值，从那时起网络在实际用途上将毫无用处，因为信号流经无效权重时永远预测 NaN 值。

当参数梯度非常大时，梯度下降参数更新可能会将参数抛得很远，进入目标函数更大的区域，从而撤销了达到当前解所做的大部分工作。

— 第413页，Deep Learning，2016。

权重下溢或溢出通常被称为网络训练过程的不稳定性，并以梯度爆炸命名，因为不稳定的训练过程会导致网络无法训练，使得模型本质上毫无用处。在给定的神经网络中，例如卷积神经网络或多层感知器，这可能是由于配置选择不当造成的。一些示例包括：

- 学习率选择不当，导致权重更新过大。
- 数据准备选择不当，允许目标变量存在较大差异。
- 损失函数选择不当，允许计算出较大的误差值。

梯度爆炸也是循环神经网络的问题，例如长短期记忆网络，因为在展开的循环结构中误差梯度会累积。一般来说，通过仔细配置网络模型，例如选择较小的学习率、缩放的目标变量和标准损失函数，可以避免梯度爆炸。尽管如此，对于具有大量输入时间步的循环网络，梯度爆炸仍可能是一个问题。

使用完整梯度训练 LSTM 时的一个困难是导数有时会变得过大，导致数值问题。为防止这种情况，我们将损失相对于 LSTM 层网络输入的导数（在应用 sigmoid 和 tanh 函数之前）裁剪到预定义范围内。

— Generating Sequences With Recurrent Neural Networks，2013。

解决梯度爆炸的常见方法是在将误差导数向后传播并用于更新权重之前对其进行更改。通过重新缩放误差导数，权重更新也会被重新缩放，从而大幅降低溢出或下溢的可能性。更新误差导数主要有两种方法；它们是：

- 梯度缩放。
- 梯度裁剪。

梯度缩放涉及归一化误差梯度向量，使向量范数（大小）等于定义值，例如 1.0。

> ... 处理梯度范数突然增加的一个简单机制是当它们超过阈值时重新缩放它们
> 
> — *On the difficulty of training Recurrent Neural Networks*，2013。

梯度裁剪涉及如果梯度超过预期范围，则将梯度值（逐元素）强制为特定的最小值或最大值。这些方法合在一起通常简称为 *梯度裁剪*。

> 当传统的梯度下降算法提出进行非常大的步长时，梯度裁剪启发式方法会介入以减小步长，使其足够小，从而不太可能超出梯度指示的近似最陡下降方向的区域。
> 
> — 第289页，*Deep Learning*，2016。

这是一种仅解决深度神经网络模型训练数值稳定性的方法，并不提供任何整体性能改进。梯度向量范数或首选范围的值可以通过试错来配置，也可以通过使用文献中常用的值，或先通过实验观察常见的向量范数或范围然后选择合理的值来配置。

> 在我们的实验中我们注意到，对于给定的任务和模型大小，训练对这个 [gradient norm] 超参数不是很敏感，即使对于相当小的阈值，算法也能表现良好。
> 
> — *On the difficulty of training Recurrent Neural Networks*，2013。

通常对网络中的所有层使用相同的梯度裁剪配置。尽管如此，存在输出层允许的误差梯度范围比隐藏层更大的示例。

> 输出导数 [...] 被裁剪到范围 [-100, 100]，而 LSTM 导数被裁剪到范围 [-10, 10]。裁剪输出梯度对于数值稳定性至关重要；即便如此，网络在训练后期有时仍会出现数值问题，在它们开始在训练数据上过拟合之后。
> 
> — Generating Sequences With Recurrent Neural Networks，2013。

## 8.2 梯度裁剪 Keras API

Keras 支持在每个优化算法上进行梯度裁剪，并将相同的方案应用于模型中的所有层。梯度裁剪可以通过在配置优化算法时包含一个额外的参数与优化算法一起使用，例如随机梯度下降。可以使用的两种梯度裁剪类型是：梯度范数缩放和梯度值裁剪。

### 8.2.1 梯度范数缩放

梯度范数缩放涉及当梯度向量的 L2 向量范数（平方值之和）超过阈值时更改损失函数的导数，使其具有给定的向量范数。例如，我们可以指定范数为 1.0，这意味着如果梯度的向量范数超过 1.0，则向量中的值将被重新缩放，使向量的范数等于 1.0。这可以在 Keras 中通过在优化器上指定 `clipnorm` 参数来使用；例如：

```
...

# configure sgd with gradient norm clipping

opt = SGD(lr=0.01, momentum=0.9, clipnorm=1.0)
```

Listing 8.1: Keras 中梯度范数缩放的示例。

### 8.2.2 梯度值裁剪

梯度值裁剪涉及如果梯度值小于负阈值或大于正阈值，则将损失函数的导数裁剪为给定值。例如，我们可以指定范数为 0.5，这意味着如果梯度值小于 -0.5，则将其设为 -0.5，如果大于 0.5，则将其设为 0.5。这可以在 Keras 中通过在优化器上指定 `clipvalue` 参数来使用，例如：

```
...
```
