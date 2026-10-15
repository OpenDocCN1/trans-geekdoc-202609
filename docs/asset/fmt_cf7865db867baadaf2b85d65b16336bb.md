
代码清单 5.36：使用 MLP 在 blobs 问题上评估自适应学习率技术动态的示例。

运行该示例会生成一个图，其中包含针对不同评估优化算法的四个折线图。训练数据集上的分类准确率用蓝色标记，测试数据集上的准确率用橙色标记。

注意：由于学习算法的随机性，你的具体结果可能会有所不同。请考虑多次运行该示例，并比较平均性能。

我们再次看到，使用默认学习率 `0.01` 且不带动量的 SGD 确实能学习该问题，但几乎需要全部 `200` 个轮次，并且在训练数据上的准确率不稳定，在测试数据集上更不稳定。图中显示，所有三种自适应学习率方法都能更快地学习问题，并且训练集和测试集准确率的波动明显更小。

RMSProp 和 Adam 表现出相似的性能，在 `50` 个训练轮次内有效学习了问题，并在剩余训练时间内进行非常微小的权重更新，但并不像我们在上一节中看到的学习率调度那样收敛。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_152_0.png)

图 5.9：在 blobs 分类问题上，一系列自适应学习率方法的训练集和测试集准确率折线图。

#### 5.4 扩展

本节列出了一些你可能希望探索的教程扩展思路。

- **调整学习率**。更新学习率实验，使其在已发现的最佳数量级内自动变化学习率。
- **初始学习率**。对于像 Adam 这样的自适应学习率方法，改变初始学习率并比较结果。

如果你探索了这些扩展中的任何一项，我很乐意知道。

#### 5.5 进一步阅读

如果你想更深入地了解该主题，本节提供了更多资源。

- 如何使用学习率调度、动量和自适应学习率进一步提高性能。

##### 5.6.1 下一步

在下一个教程中，你将了解学习过程如何对输入和目标变量的尺度敏感，以及数据归一化和标准化如何对收敛产生显著影响。

## 第 6 章

## 用数据缩放稳定学习

深度学习神经网络从训练数据集中的示例学习如何将输入映射到输出。模型的权重被初始化为小的随机值，并根据训练数据集上的误差估计通过优化算法进行更新。鉴于模型使用小权重，并且使用预测值与实际值之间的误差，用于训练模型的输入和输出的尺度是一个重要因素。未缩放的输入变量可能导致学习过程缓慢或不稳定，而回归问题中未缩放的目标变量可能导致梯度爆炸，从而使学习过程失败。数据准备包括在训练神经网络模型之前，使用归一化和标准化等技术重新缩放输入和输出变量。在本教程中，你将了解如何通过数据缩放来提高神经网络的稳定性和建模性能。完成本教程后，你将了解：

- 在处理深度学习神经网络时，数据缩放是推荐的预处理步骤。
- 数据缩放可以通过对实值输入和输出变量进行归一化或标准化来实现。
- 如何应用标准化和归一化来提高多层感知器模型在回归预测建模问题上的性能。

让我们开始吧。

## 6.1 数据缩放

在本节中，你将了解数据缩放、它在训练期间对模型的影响，以及在训练自己的神经网络模型时如何缩放输入和目标变量的技巧。

### 6.1.1 数据的尺度很重要

深度学习神经网络模型学习从输入变量到输出变量的映射。因此，每个变量的数据尺度和分布可能不同。输入变量可能具有不同的单位（例如英尺、公里和小时），这反过来可能意味着这些变量

不同变量具有不同的尺度。输入变量尺度的差异可能会增加建模问题的难度。例如，较大的输入值（如分布范围达数百或数千个单位）可能导致模型学习到较大的权重值。具有较大权重值的模型往往不稳定，这意味着它在学习过程中可能表现不佳，并且对输入值敏感，从而导致更高的泛化误差。

最常见的预处理形式之一是对输入变量进行简单的线性重新缩放。

> — 第298页，《模式识别的神经网络》，1995年。

反过来，目标变量值分布范围较大可能导致较大的误差梯度值，从而引起权重值剧烈变化，使学习过程不稳定。缩放输入和输出变量是使用神经网络模型时的关键步骤。

在实践中，在将输入数据呈现给网络之前，几乎总是有利的。同样，网络的输出通常也会经过后处理，以给出所需的输出值。

> — 第296页，《模式识别的神经网络》，1995年。

### 6.1.2 缩放输入变量

输入变量是网络在输入层或可见层接收以进行预测的变量。一个经验法则是输入变量应为小值，通常在0-1的范围内，或者经过标准化使其均值为零、标准差为一。输入变量是否需要缩放取决于你的问题及每个变量的具体情况。你可能有一系列量作为输入，例如价格或温度。

缩放可以加速学习，因为它有助于平衡连接到输入节点的权重的学习速率。

> — Efficient BackProp，1998年。

如果量的分布是正态分布，则应进行标准化，否则应进行归一化。这适用于量值范围较大（如10、100等）或较小（如0.01、0.0001）的情况。如果量值较小（接近0-1）且分布有限（如标准差接近1），那么也许可以不进行数据缩放。问题可能很复杂，如何最好地缩放输入数据可能并不明确。如有疑问，可对输入序列进行归一化。如果资源允许，可尝试分别使用原始数据、标准化数据和归一化数据进行建模，看看最终模型性能是否存在有益的差异。

如果输入变量是线性组合的，如MLP（多层感知器），那么至少在理论上，很少有必要对输入进行标准化。 [...] 然而，出于多种实际原因，对输入进行标准化可以使训练更快，并减少陷入局部最优的机会。

> — 是否应对数据进行归一化/标准化/重新缩放？神经网络常见问题解答。

### 6.1.3 缩放输出变量

输出变量是网络预测的变量。你必须确保输出变量的尺度与网络输出层激活函数（传递函数）的尺度匹配。

如果你的输出激活函数范围是[0,1]，那么显然你必须确保目标值位于该范围内。但是，通常选择适合目标分布的输出激活函数比强制数据符合输出激活函数更好。

> — 是否应对数据进行归一化/标准化/重新缩放？神经网络常见问题解答。

如果你的问题是回归问题，那么输出将是一个实数值。这最好使用线性激活函数建模。如果该值的分布是正态分布，则可以标准化输出变量。否则，可将输出变量进行归一化。

## 6.2 数据缩放 scikit-learn API

你可能需要考虑两种数据缩放类型：归一化和标准化。这两种都可以使用`scikit-learn`库实现。

### 6.2.1 数据归一化

归一化是将数据从原始范围重新缩放，使所有值都在0到1的范围内。归一化要求你已知或能够准确估计可观测值的最小值和最大值。你可能可以从现有数据中估计这些值。如果要归一化的x值超出了最小值和最大值的边界，则结果值将不在0到1的范围内。你可以在进行预测之前检查这些观测值，并将其从数据集中移除或将其限制在预定义的最大值或最小值范围内。你可以使用`scikit-learn`的`MinMaxScaler`对象来归一化数据集。使用`MinMaxScaler`及其他缩放技术的良好实践如下：

- **使用可用的训练数据拟合缩放器。** 对于归一化，这意味着用训练数据来估计可观测的最小值和最大值。可通过调用`fit()`函数完成。
- **将缩放应用于训练数据。** 这意味着你可以使用归一化后的数据来训练模型。可通过调用`transform()`函数完成。
- **将缩放应用于后续数据。** 这意味着你可以为将来要预测的新数据处理做准备。

`MinMaxScaler`的默认缩放范围是[0,1]，但可以通过`feature_range`参数指定首选范围，并传入包含所有变量的最小值和最大值的元组。

```python
# create scaler

scaler = MinMaxScaler(feature_range=(-1,1))
```

代码6.1：定义`MinMaxScaler`的示例。

如果需要，可以反转变换。这对于将预测结果转换回原始尺度以进行报告或绘图非常有用。可通过调用`inverse_transform()`函数完成。下面的示例演示了使用`MinMaxScaler`归一化数据的一般方法。

```python
# demonstrate data normalization with sklearn

from sklearn.preprocessing import MinMaxScaler

# load data

data = ...

# create scaler

scaler = MinMaxScaler()

# fit scaler on data

scaler.fit(data)

# apply transform

normalized = scaler.transform(data)

# inverse transform

inverse = scaler.inverse_transform(normalized)
```

代码6.2：使用`MinMaxScaler`的示例。

你还可以使用`fit_transform()`函数在一步中同时完成拟合和变换；例如：

```python
# demonstrate data normalization with sklearn

from sklearn.preprocessing import MinMaxScaler

# load data

data = ...

# create scaler

scaler = MinMaxScaler()

# fit and transform in one step

normalized = scaler.fit_transform(data)

# inverse transform

inverse = scaler.inverse_transform(normalized)
```

代码6.3：使用`MinMaxScaler`的另一种方式的示例。

### 6.2.2 数据标准化

标准化数据集涉及重新缩放值的分布，使观测值的均值为0，标准差为1。它有时被称为白化。可以将其理解为减去均值或使数据中心化。与归一化类似，当你的数据包含尺度不同的输入值时，标准化在某些机器学习算法中可能是有用的，甚至可能是必需的。标准化假设你的观测值符合高斯分布（钟形曲线），且均值和标准差表现良好。如果数据不符合这一预期，你仍然可以标准化数据，但可能得不到可靠的结果。对于神经网络来说，标准化可能是更可取的数据准备方案。

如果训练集上每个输入变量的平均值接近零，收敛通常会更快。

> — *Efficient BackProp*，1998年。

标准化要求你已知或能够准确估计可观测值的均值和标准差。你可以从训练数据中估计这些值。你可以使用`scikit-learn`的`StandardScaler`对象对数据集进行标准化。

```python
# demonstrate data standardization with sklearn

from sklearn.preprocessing import StandardScaler

# load data

data = ...

# create scaler

scaler = StandardScaler()

# fit scaler on data

scaler.fit(data)

# apply transform

standardized = scaler.transform(data)

# inverse transform

inverse = scaler.inverse_transform(standardized)
```

代码6.4：使用`StandardScaler`的示例。

你还可以使用`fit_transform()`函数在一步中同时完成拟合和变换；例如：

```python
# demonstrate data standardization with sklearn

from sklearn.preprocessing import StandardScaler

# load data

data = ...

# create scaler

scaler = StandardScaler()

# fit and transform in one step

standardized = scaler.fit_transform(data)

# inverse transform

inverse = scaler.inverse_transform(standardized)
```

代码6.5：使用`StandardScaler`的另一种方式的示例。

## 6.3 数据缩放案例研究

在本节中，我们将演示如何在简单的分类问题上使用数据缩放来改进MLP的收敛。该示例为你在分类和回归问题中使用自己的神经网络探索数据缩放提供了一个模板。

### 6.3.1 回归预测建模问题

回归预测建模问题涉及预测一个实值数量。我们可以使用`scikit-learn`库中`make_regression()`函数提供的标准回归问题生成器。该函数将从一个简单的回归问题中生成示例，该问题具有给定数量的输入变量、统计噪声和其他属性。我们将使用该函数定义一个具有20个输入特征的问题；其中10个特征是有意义的，10个是无关的。将随机生成总共1000个示例。伪随机数生成器将被固定，以确保每次运行代码时我们得到相同的1000个示例。

```python
# generate regression dataset

X, y = make_regression(n_samples=1000, n_features=20, noise=0.1, random_state=1)
```

清单6.6：生成回归问题样本的示例。

每个输入变量都服从高斯分布，目标变量也是如此。我们可以通过绘制部分输入变量和输出变量的直方图来证明这一点。

```python
# regression predictive modeling problem

from sklearn.datasets import make_regression

from matplotlib import pyplot

# generate regression dataset

X, y = make_regression(n_samples=1000, n_features=20, noise=0.1, random_state=1)

# histograms of input variables

pyplot.subplot(211)

pyplot.hist(X[:, 0])

pyplot.subplot(212)

pyplot.hist(X[:, 1])

pyplot.show()

# histogram of target variable

pyplot.hist(y)

pyplot.show()
```

清单6.7：生成样本并绘制回归问题分布的示例。

运行该示例会生成两个图。第一个图显示了二十个输入变量中前两个变量的直方图，表明每个变量都服从高斯数据分布。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_161_0.png)

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_161_1.png)

图6.1：回归问题中二十个输入变量中两个变量的直方图。

第二个图显示了目标变量的直方图，表明该变量的取值范围比输入变量大得多，并且同样呈现高斯数据分布。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_162_0.png)

图6.2：回归问题中目标变量的直方图。

既然我们有了一个可以作为研究基础的回归问题，我们就可以开发一个模型来解决它。

### 6.3.2 使用未缩放数据的多层感知机

我们可以为回归问题开发一个多层感知机（MLP）模型。该模型将在原始数据上进行演示，不对输入或输出变量进行任何缩放。我们预期模型性能通常会较差。第一步是将数据划分为训练集和测试集，以便我们能够拟合和评估模型。我们将从该域中生成1,000个样本，并将数据集一分为二，使用500个样本作为训练集和测试集。

```python
# split into train and test

n_train = 500

trainX, testX = X[:n_train, :], X[n_train:, :]

trainy, testy = y[:n_train], y[n_train:]
```

清单6.8：为建模准备数据集的示例。

接下来，我们可以定义MLP模型。模型将期望接收问题中的20个输入变量，即20个输入。将使用一个具有25个节点和修正线性激活函数的隐藏层。输出层有一个节点，对应于单个目标变量，并使用线性激活函数直接预测实数值。

```python
# define model

model = Sequential()

model.add(Dense(25, input_dim=20, activation='relu', kernel_initializer='he_uniform'))

model.add(Dense(1, activation='linear'))
```

清单6.9：定义MLP模型的示例。

将使用均方误差损失函数来优化模型，并采用随机梯度下降优化算法，其合理的默认配置为学习率0.01和动量0.9。

```python
# compile model

model.compile(loss='mean_squared_error', optimizer=SGD(lr=0.01, momentum=0.9))
```

清单6.10：编译MLP模型的示例。

模型将训练100个轮次，测试集将用作验证集，并在每个训练轮次结束时进行评估。训练结束时，计算训练集和测试集上的均方误差，以了解模型对问题的学习效果。

```python
# evaluate the model

train_mse = model.evaluate(trainX, trainy, verbose=0)

test_mse = model.evaluate(testX, testy, verbose=0)
```

清单6.11：评估MLP模型的示例。

最后，使用折线图绘制每个训练轮次结束时训练集和测试集上的均方误差学习曲线，以了解模型在学习该问题时的动态变化。

```python
# plot loss during training

pyplot.title('Mean Squared Error')

pyplot.plot(history.history['loss'], label='train')

pyplot.plot(history.history['val_loss'], label='test')

pyplot.legend()

pyplot.show()
```
