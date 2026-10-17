
# reshape 1d arrays to 2d arrays

```
trainy = trainy.reshape(len(trainy), 1)

testy = testy.reshape(len(trainy), 1)

# fit scaler on training dataset

output_scaler.fit(trainy)

# transform training dataset

trainy = output_scaler.transform(trainy)

# transform test dataset

testy = output_scaler.transform(testy)

return trainX, trainy, testX, testy
```

# fit and evaluate mse of model on test set

```
def evaluate_model(trainX, trainy, testX, testy):

    # define model

    model = Sequential()

    model.add(Dense(25, input_dim=20, activation='relu', kernel_initializer='he_uniform'))

    model.add(Dense(1, activation='linear'))

    # compile model

    model.compile(loss='mean_squared_error', optimizer=SGD(lr=0.01, momentum=0.9))

    # fit model

    model.fit(trainX, trainy, epochs=100, verbose=0)

    # evaluate the model

    test_mse = model.evaluate(testX, testy, verbose=0)

    return test_mse
```

# evaluate model multiple times with given input and output scalers

```
def repeated_evaluation(input_scaler, output_scaler, n_repeats=30):

    # get dataset

    trainX, trainy, testX, testy = get_dataset(input_scaler, output_scaler)

    # repeated evaluation of model

    results = list()

    for _ in range(n_repeats):

        test_mse = evaluate_model(trainX, trainy, testX, testy)

        print('%.3f' % test_mse)

        results.append(test_mse)

    return results
```

# unscaled inputs

```
results_unscaled_inputs = repeated_evaluation(None, StandardScaler())

# normalized inputs

results_normalized_inputs = repeated_evaluation(MinMaxScaler(), StandardScaler())

# standardized inputs

results_standardized_inputs = repeated_evaluation(StandardScaler(), StandardScaler())

# summarize results

print('Unscaled: %.3f (%.3f)' % (mean(results_unscaled_inputs),

    std(results_unscaled_inputs)))

print('Normalized: %.3f (%.3f)' % (mean(results_normalized_inputs),

    std(results_normalized_inputs)))

print('Standardized: %.3f (%.3f)' % (mean(results_standardized_inputs),

    std(results_standardized_inputs)))

# plot results

results = [results_unscaled_inputs, results_normalized_inputs, results_standardized_inputs]

labels = ['unscaled', 'normalized', 'standardized']

pyplot.boxplot(results, labels=labels)

pyplot.show()
```

列表 6.23：使用不同方法缩放输入评估 MLP 模型的示例。

运行示例会在过程中打印每个模型运行的均方误差。在每个三个配置都评估 30 次后，会报告每个配置的平均误差。

**Note:** 由于学习算法的随机性，您的具体结果可能会有所不同。请考虑多次运行示例并比较平均性能。

在这种情况下，我们可以看到，正如我们所预期的那样，缩放输入变量确实会带来性能更好的模型。令人意外的是，使用归一化输入而不是标准化输入可以看到更好的性能。这可能与第一隐藏层中整流线性激活函数的选择有关。

```
...

>0.010

>0.012

>0.005

>0.008

>0.008

Unscaled: 0.007 (0.004)

Normalized: 0.001 (0.000)

Standardized: 0.008 (0.004)
```

列表 6.24：使用不同方法缩放输入评估 MLP 模型的示例输出。

创建了一个包含三个箱线图的图形，总结了每个配置的误差分数的分布情况。图表显示，未缩放输入变量和标准化输入变量的误差分数分布之间几乎没有差异，而归一化输入变量会导致更好的性能以及更稳定或更紧凑的误差分数分布。

这些结果强调，实际实验并确认数据缩放方法的结果非常重要，而不是根据观察到的数据分布来假设某个数据准备方案会效果最佳。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_172_0.png)

图6.4：回归问题中未缩放、归一化和标准化输入变量的均方误差箱线图。

## 6.4 扩展

本节列出了一些你可能希望探索的教程扩展想法。

- **归一化目标变量**：更新示例，对目标变量进行归一化而非标准化，并比较结果。
- **比较目标变量的缩放方式**：更新示例，通过重复实验比较目标变量的标准化和归一化，并比较结果。
- **其他缩放范围**：更新示例，在归一化时评估其他最小/最大范围，例如 \[-1, 1\] 和 \[0.0, 0.5\]，并比较性能。

如果你探索了这些扩展中的任何一项，我很想知道。

## 6.5 延伸阅读

如果你想深入了解，本节提供了更多关于该主题的资源。

### 6.5.1 书籍

- 第8.2节：输入归一化与编码，*模式识别的神经网络*，1995年。 https://amzn.to/2S8qdwt

### 6.5.2 论文

- *高效反向传播*，1998年。 http://yann.lecun.com/exdb/publis/pdf/lecun-98b.pdf

### 6.5.3 API

- sklearn.datasets.make_regression API。 http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_regression.html
- sklearn.preprocessing.MinMaxScaler API。 http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html
- sklearn.preprocessing.StandardScaler API。 http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html

### 6.5.4 文章

- 我应该对数据进行归一化/标准化/重新缩放吗？神经网络常见问题解答。 ftp://ftp.sas.com/pub/neural/FAQ2.html#A_std

## 6.6 总结

在本教程中，你学习了如何通过缩放数据来提高神经网络的稳定性和建模性能。具体来说，你学到了：

- 数据缩放是使用深度学习神经网络时推荐的预处理步骤。
- 数据缩放可以通过对实值输入和输出变量进行归一化或标准化来实现。
- 如何应用标准化和归一化来提高多层感知机模型在回归预测建模问题上的性能。

### 6.6.1 下一步

在下一个教程中，你将了解如何通过使用修正线性激活函数来解决梯度消失问题。

## 第7章

## 使用ReLU修复梯度消失

在神经网络中，激活函数负责将节点的加权求和输入转换为该节点的激活值或该输入的输出。修正线性激活函数是一个分段线性函数，如果输入为正，则直接输出该输入；否则，输出零。它已成为许多类型神经网络默认的激活函数，因为使用它的模型更容易训练，并且通常能获得更好的性能。在本教程中，你将了解用于深度学习神经网络的修正线性激活函数。完成本教程后，你将知道：

- 由于梯度消失问题，sigmoid和双曲正切激活函数不能用于多层网络。
- 修正线性激活函数克服了梯度消失问题，使模型能够更快地学习并表现得更好。
- 在开发多层感知机和卷积神经网络时，修正线性激活是默认的激活函数。

让我们开始吧。

## 7.1 梯度消失与ReLU

在本节中，你将了解梯度消失问题、它在训练过程中对模型的影响，以及如何使用修正线性激活函数来解决该问题。

### 7.1.1 Sigmoid和Tanh激活函数的局限性

神经网络由多层节点组成，学习将输入示例映射到输出。对于给定节点，输入乘以该节点的权重并求和。这个值称为节点的求和激活。然后通过激活函数对求和激活进行转换，定义该节点的特定输出或激活。最简单的激活函数称为线性激活，即完全不进行转换。仅由线性激活函数组成的网络非常容易训练，但无法学习复杂的映射函数。线性激活函数仍然用于预测数值的网络输出层（例如回归问题）。

非线性激活函数更受青睐，因为它们允许节点学习数据中更复杂的结构。传统上，两种广泛使用的非线性激活函数是sigmoid和双曲正切激活函数。sigmoid激活函数（也称为逻辑函数）历来是神经网络中非常流行的激活函数。函数的输入被转换为0.0到1.0之间的值。远大于1.0的输入被转换为1.0；同样，远小于0.0的值被截断为0.0。该函数在所有可能输入上的形状是从0开始，经过0.5，上升到1.0的S形。在直到1990年代初的很长一段时间里，它是神经网络使用的默认激活函数。双曲正切函数（简称tanh）是一种形状相似的非线性激活函数，输出值介于-1.0和1.0之间。在1990年代后期到2000年代，tanh函数比sigmoid激活函数更受青睐，因为使用它的模型更容易训练，而且通常具有更好的预测性能。

> ……双曲正切激活函数通常比逻辑sigmoid表现更好。

—— 第195页，《深度学习》，2016年。

sigmoid和tanh函数的一个普遍问题是它们会饱和。这意味着，对于tanh和sigmoid，大值分别被截断为1.0，小值被截断为-1或0。此外，这些函数实际上只对其输入中点附近的变化敏感，例如sigmoid的0.5和tanh的0.0。无论来自节点的求和激活作为输入是否包含有用信息，函数的有限敏感性和饱和都会发生。一旦饱和，学习算法就难以继续调整权重以提高模型性能。

> ……sigmoid单元在其大部分定义域内都会饱和——当z非常大时，它们饱和到高值；当z非常负时，饱和到低值；只有当z接近0时，它们才对输入强烈敏感。

—— 第195页，《深度学习》，2016年。

最后，随着GPU带来的硬件能力提升，使用sigmoid和tanh激活函数的非常深的神经网络难以训练。使用这些非线性激活函数的大型网络中的深层无法获得有用的梯度信息。误差通过网络反向传播，并用于更新权重。由于所选激活函数的导数，误差量在每额外传播一层时都会急剧减少。这被称为梯度消失问题，它会阻止深度（多层）网络有效学习。

> 梯度消失使得难以确定参数应向哪个方向移动以改进代价函数

—— 第290页，《深度学习》，2016年。

尽管使用非线性激活函数使神经网络能够学习复杂的映射函数，但它们实际上阻止了学习算法处理深度网络。在2000年代末和2010年代初，人们通过使用其他网络类型（如玻尔兹曼机）以及逐层训练或无监督预训练找到了变通方法。

### 7.1.2 矫正线性激活函数

为了使用随机梯度下降与误差反向传播来训练深度神经网络，需要一种看起来和表现像线性函数，但实际上是非线性函数、能够学习数据中复杂关系的激活函数。该函数还必须对激活和输入提供更高的敏感度，并避免容易饱和。该解决方案在该领域已流传一段时间，但直到 2009 年和 2011 年的论文将其凸显出来才受到关注。解决方案是使用矫正线性激活函数，简称 ReLU。实现该激活函数的节点或单元被称为矫正线性激活单元，简称 ReLU。通常，使用整流函数作为隐藏层的网络被称为整流网络。

采用 ReLU 很容易被视为深度学习革命中的少数里程碑之一，例如现在允许常规开发非常深的神经网络的技术。

> [another] 大大改善了前馈网络性能的一个主要算法变化是将 sigmoid 隐藏单元替换为分段线性隐藏单元，例如矫正线性单元。
> 
> — 第 226 页，《Deep Learning》，2016 年。

矫正线性激活函数是一个简单的计算，它直接返回作为输入提供的值，如果输入小于或等于 0.0，则返回值为 0.0。我们可以用一个简单的 if 语句来描述它：

```
if input > 0:
    return input
else:
    return 0
```

列表 7.1：使用 if 语句的矫正线性激活函数示例。

我们可以用 max() 函数在集合 {0.0, 输入 z} 上数学地描述该函数 g()；例如：

g(z) = max{0, z}    (7.1)

该函数对于大于零的值是线性的，这意味着在使用反向传播训练神经网络时，它具有许多线性激活函数的理想特性。然而，它是非线性函数，因为负值始终输出为零。

> 因为矫正线性单元几乎是线性的，它们保留了使线性模型易于用基于梯度的方法优化的许多特性。它们也保留了使线性模型泛化良好的许多特性。
> 
> — 第 175 页，《Deep Learning》，2016 年。

因为整流函数在输入域的一半上是线性的，在另一半上是非线性的，所以它被称为分段线性函数或铰链函数。

然而，从它是具有两个线性片段的分段线性函数这一意义上讲，该函数仍然非常接近线性。

现在我们熟悉了矫正线性激活函数，让我们看看如何在 Python 中实现它。

### 7.1.3 如何实现矫正线性激活函数

我们可以很容易地在 Python 中实现矫正线性激活函数。也许最简单的实现是使用 max() 函数；例如：

```
# rectified linear function
def rectified(x):
    return max(0.0, x)
```

列表 7.2：矫正线性激活函数的示例实现。

我们期望任何正值都将被原样返回，而输入值为 0.0 或负值将被返回为 0.0。下面是矫正线性激活函数的一些输入和输出示例。

```
# demonstrate the rectified linear function
# rectified linear function
def rectified(x):
    return max(0.0, x)

# demonstrate with a positive input
x = 1.0
print('rectified(%.1f) is %.1f' % (x, rectified(x)))
x = 1000.0
print('rectified(%.1f) is %.1f' % (x, rectified(x)))

# demonstrate with a zero input
x = 0.0
print('rectified(%.1f) is %.1f' % (x, rectified(x)))

# demonstrate with a negative input
x = -1.0
print('rectified(%.1f) is %.1f' % (x, rectified(x)))
x = -1000.0
print('rectified(%.1f) is %.1f' % (x, rectified(x)))
```

列表 7.3：使用矫正线性激活函数的变换示例。

运行示例，我们可以看到正值无论大小都会被返回，而负值会被截断为 0.0。

```
rectified(1.0) is 1.0
rectified(1000.0) is 1000.0
rectified(0.0) is 0.0
rectified(-1.0) is 0.0
rectified(-1000.0) is 0.0
```

列表 7.4：使用矫正线性激活函数变换的示例输出。

我们可以通过绘制一系列输入和计算得到的输出来了解函数输入与输出之间的关系。下面的示例生成从 -10 到 10 的整数序列，并为每个输入计算矫正线性激活，然后绘制结果。

```
# plot inputs and outputs
from matplotlib import pyplot

# rectified linear function
def rectified(x):
    return max(0.0, x)
```
