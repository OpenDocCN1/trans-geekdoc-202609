
## 回归问题

这是一个预测实值数量的问题。

-   **输出层配置：** 一个节点，使用线性激活单元。
-   **损失函数：** 均方误差（MSE）。

## 二元分类问题

这是一个将示例分类为两个类别之一的问题。该问题被表述为预测示例属于类别一的可能性，例如你将整数值 1 分配给的类别，而另一类别分配的值为 0。

-   **输出层配置：** 一个节点，使用 sigmoid 激活单元。
-   **损失函数：** 交叉熵，也称为对数损失。

## 多类分类问题

这是一个将示例分类为两个以上类别之一的问题。该问题被表述为预测示例属于每个类别的可能性。

-   **输出层配置：** 为每个类别使用 softmax 激活函数的一个节点。
-   **损失函数：** 交叉熵，也称为对数损失。

## 4.1.6 如何实现损失函数

为了使损失函数具体化，本节解释了每种主要类型的损失函数的工作原理以及如何在 Python 中计算分数。

### 均方误差损失

均方误差损失，简称 MSE，是预测值与实际值之间平方差的平均值。结果始终为正值，与预测值和实际值的符号无关，完美值为 0.0。损失值被最小化，尽管可以通过使分数为负在最大化优化过程中使用它。下面的 Python 函数提供了类似伪代码的可工作实现，用于计算实际值列表和预测实值数量列表的均方误差。

```
# calculate mean squared error
def mean_squared_error(actual, predicted):
    sum_square_error = 0.0
    for i in range(len(actual)):
        sum_square_error += (actual[i] - predicted[i])**2.0
    mean_square_error = 1.0 / len(actual) * sum_square_error
    return mean_square_error
```

Listing 4.1: 实现均方误差的函数示例。

为了高效实现，我建议你使用 scikit-learn 的 mean_squared_error() 函数¹。

### 交叉熵损失（或对数损失）

交叉熵损失通常简称为交叉熵、对数损失、逻辑损失或简称 log loss。每个预测概率与实际类别输出值（0 或 1）进行比较，并计算一个分数，该分数根据与期望值的距离对概率进行惩罚。惩罚是对数形式的，对于小的差异（0.1 或 0.2）提供较小的分数，而对于大的差异（0.9 或 1.0）提供巨大的分数。

交叉熵损失被最小化，其中较小的值代表比较大的值更好的模型。预测完美概率的模型具有 0.0 的交叉熵或对数损失。对于二元或两类预测问题，交叉熵实际上是所有示例的平均交叉熵。下面的 Python 函数提供了类似伪代码的可工作实现，用于计算实际 0 和 1 值列表与类别 1 的预测概率相比的交叉熵。

```
from math import log

# calculate binary cross-entropy
def binary_cross_entropy(actual, predicted):
    sum_score = 0.0
    for i in range(len(actual)):
        sum_score += actual[i] * log(1e-15 + predicted[i])
    mean_sum_score = 1.0 / len(actual) * sum_score
    return -mean_sum_score
```

Listing 4.2: 实现二元交叉熵的函数示例。

注意，我们在预测概率中添加一个很小的值（在本例中为 1E-15），以避免计算 0.0 的对数。这意味着在实践中，最佳可能的损失将是一个非常接近零但不完全为零的值。交叉熵可以用于多类分类计算。类别已被独热编码，这意味着每个类别值都有一个二进制特征，并且预测必须为每个类别提供预测概率。然后交叉熵在每个二进制特征上求和，并在数据集中所有示例上取平均。下面的 Python 函数提供了类似伪代码的可工作实现，用于计算实际独热编码值列表与每个类别的预测概率相比的交叉熵。

```
from math import log

# calculate categorical cross-entropy
def categorical_cross_entropy(actual, predicted):
    sum_score = 0.0
    for i in range(len(actual)):
        for j in range(len(actual[i])):
            sum_score += actual[i][j] * log(1e-15 + predicted[i][j])
    mean_sum_score = 1.0 / len(actual) * sum_score
    return -mean_sum_score
```

Listing 4.3: 实现多类交叉熵的函数示例。

为了高效实现，我建议你使用 scikit-learn 的 `log_loss()` 函数²。

## 4.1.7 损失函数与报告的模型性能

在最大似然的框架下，我们通常希望使用交叉熵或均方误差损失函数与随机梯度下降一起使用。尽管如此，我们可能希望也可能不希望使用损失函数来报告模型的性能。例如，对数损失很难解释，特别是对于非机器学习从业者利益相关者而言。均方误差也是如此。相反，对于分类和回归模型，报告准确率和均方根误差可能更为重要。

根据这些指标而不是损失来选择模型也可能是可取的。这是一个重要的考虑因素，因为损失最小的模型可能不是对项目利益相关者重要的最佳指标模型。一个好的划分是使用损失来评估和诊断模型学习得如何。这包括优化过程的所有考虑因素，例如过拟合、欠拟合和收敛。然后可以选择一个对项目利益相关者有意义的替代指标，以评估模型性能并进行模型选择。

-   **损失**：仅用于评估和诊断模型优化。
-   **指标**：用于在项目背景下评估和选择模型。

同一个指标可以用于这两个关注点，但优化过程的关注点更可能与项目的目标不同，需要不同的分数。尽管如此，通常情况下，改进损失会改善指标，或在最坏情况下对感兴趣的指标没有影响。

## 4.2 回归损失函数案例研究

回归预测建模问题涉及预测实值数量。在本节中，我们将研究适合回归预测建模问题的损失函数。作为本次研究的背景，我们将使用 scikit-learn 库中提供的标准回归问题生成器 `make_regression()` 函数。该函数将从具有给定数量输入变量、统计噪声和其他属性的简单回归问题生成示例。我们将使用此函数定义一个具有 20 个输入特征的问题；其中 10 个特征是有意义的，10 个特征与问题无关。总共将随机生成 1,000 个示例。伪随机数生成器将被固定，以确保每次运行代码时都获得相同的 1,000 个示例。

```
# generate regression dataset
X, y = make_regression(n_samples=1000, n_features=20, noise=0.1, random_state=1)
```

Listing 4.4: 为回归问题生成样本的示例。

神经网络在实值输入和输出变量缩放到合理范围时通常表现更好。对于这个问题，每个输入变量和目标变量都具有高斯分布；因此，在这种情况下标准化数据是可取的。我们可以使用 scikit-learn 库中的 StandardScaler 转换器类来实现这一点。在实际问题中，我们会在训练数据集上准备缩放器并将其应用于训练集和测试集，但为了简单起见，我们将在拆分为训练集和测试集之前一起缩放所有数据。

```
# standardize dataset
X = StandardScaler().fit_transform(X)
y = StandardScaler().fit_transform(y.reshape(len(y),1))[:,0]
```

Listing 4.5: 标准化数据样本的示例。

缩放后，数据将被均匀拆分为训练集和测试集。

```
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
```

Listing 4.6: 将数据拆分为训练集和测试集的示例。

将定义一个小型多层感知器（MLP）模型来解决此问题并为探索不同的损失函数提供基础。模型将期望 20 个特征作为输入，如问题所定义。模型将有一个隐藏层，包含 25 个节点，并使用整流线性激活函数。输出层将有 1 个节点，因为要预测一个实值，并将使用线性激活函数。

```
# define model
model = Sequential()
model.add(Dense(25, input_dim=20, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(1, activation='linear'))
```

Listing 4.7: 定义 MLP 模型的示例。

模型将使用学习率为 0.01、动量为 0.9 的随机梯度下降进行拟合，这两者都是合理的默认值。训练将在 100 个 epoch 上进行，并在每个 epoch 结束时评估测试集，以便在运行结束时绘制学习曲线。

```
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='...', optimizer=opt)
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=100, verbose=0)
```

Listing 4.8: 编译和拟合 MLP 模型的示例。

现在我们有了问题和模型的基础，我们可以评估三种常见的损失函数，这些损失函数适用于回归预测建模问题。尽管这些示例中使用了 MLP，但相同的损失函数也可以在为回归训练 CNN 和 RNN 模型时使用。
