

```python
print('(P)---')
for i, x in enumerate(unique):
    print("%s| %s" % (x, ' '.join(str(x) for x in matrix[i])))

# Test confusion matrix with integers
actual = [0,0,0,0,0,1,1,1,1,1]
predicted = [0,1,1,0,0,1,0,1,1,1]
unique, matrix = confusion_matrix(actual, predicted)
print_confusion_matrix(unique, matrix)
```

清单 4.10：计算并显示漂亮混淆矩阵的示例。

运行示例会产生以下输出。我们可以看到顶部和底部的类标签为 0 和 1。从左上角到右下角沿着矩阵对角线向下看，我们可以看到 3 次对 0 的预测是正确的，4 次对 1 的预测是正确的。

查看其他单元格，我们可以看到 2 + 1 或 3 个预测错误。我们可以看到有 2 次预测被标记为 1，但实际上是 0 类别值。我们可以看到有 1 次预测被标记为 0，但实际上是 1。

```text
(A)0 1
(P)---
0| 3 1
1| 2 4
```

清单 4.11：打印漂亮混淆矩阵的示例输出。

混淆矩阵始终是一个好主意，可以在分类准确率之外使用，以帮助解释预测。

### 4.2.3 平均绝对误差

回归问题是那些预测真实值的问题。一个容易考虑的指标是预测值与预期值相比的误差。平均绝对误差（MAE）是一个很好的首选误差指标。它是通过绝对误差值的平均值计算得出的，其中 *绝对* 意味着变为正数，以便可以相加在一起。

$$MAE = \frac{\sum_{i=1}^{n} abs(predicted_i - actual_i)}{\text{total predictions}} \tag{4.2}$$

下面是一个名为 `mae_metric()` 的函数，它实现了这个指标。与上面一样，它期望一组实际结果值和一组预测值。我们使用内置的 `abs()` Python 函数来计算相加在一起的绝对误差值。

```python
# Calculate mean absolute error
def mae_metric(actual, predicted):
    sum_error = 0.0
    for i in range(len(actual)):
        sum_error += abs(predicted[i] - actual[i])
    return sum_error / float(len(actual))
```

清单 4.12：计算平均绝对误差的函数。

我们可以编造一个小回归数据集来测试这个函数。

```python
# Calculate root mean squared error
def rmse_metric(actual, predicted):
    sum_error = 0.0
    for i in range(len(actual)):
        prediction_error = predicted[i] - actual[i]
        sum_error += (prediction_error ** 2)
    mean_error = sum_error / float(len(actual))
    return sqrt(mean_error)
```

清单 4.16：计算均方根误差的函数。

我们可以在上面用于测试平均绝对误差计算的同一数据集上测试这个指标。下面是一个完整示例。同样，我们期望误差值通常接近 0.01。

```python
# Example of Calculating the Root Mean Squared Error
from math import sqrt

# Calculate root mean squared error
def rmse_metric(actual, predicted):
    sum_error = 0.0
    for i in range(len(actual)):
        prediction_error = predicted[i] - actual[i]
        sum_error += (prediction_error ** 2)
    mean_error = sum_error / float(len(actual))
    return sqrt(mean_error)

# Test RMSE
actual = [0.1, 0.2, 0.3, 0.4, 0.5]
predicted = [0.11, 0.19, 0.29, 0.41, 0.5]
rmse = rmse_metric(actual, predicted)
print(rmse)
```

清单 4.17：计算均方根误差的示例。

运行示例，我们看到以下结果。结果略高，为 0.0089。RMSE 值始终略高于 MSE 值，随着预测误差增加，这种差异会更加明显。使用 RMSE 而非 MSE 的好处在于，它会用更差的分数来惩罚较大的误差。

```text
0.00894427191
```

清单 4.18：计算均方根误差的示例输出。

### 4.3 扩展

你只看到了最广泛使用的性能指标的一个小样本。还有许多其他性能指标你可能需要。下面是 5 个你可能希望实现以扩展本教程的额外性能指标列表：

- 分类的精确率。
- 分类的召回率。
- 分类的 F1 分数。
- 分类的 ROC 曲线下面积或 AUC。
- 回归的拟合优度或 $R^2$（R 平方）。

### 4.4 回顾

在本教程中，你了解了如何在 Python 中从头实现算法预测性能指标。具体来说，你学习了：

- 如何实现和解释分类准确率。
- 如何实现和解释分类问题的混淆矩阵。
- 如何实现和解释回归的平均绝对误差。
- 如何实现和解释回归的均方根误差。

### 4.4.1 进一步阅读

- 第 9.2 节，数学函数，*Python 标准库* https://docs.python.org/2/library/math.html

### 4.4.2 下一步

在下一个教程中，你将了解如何在预测建模问题上建立性能基线。

## 第 5 章：基线模型

在预测建模问题上建立基线性能很重要。基线为你稍后评估的更高级方法提供了比较点。在本教程中，你将了解如何在 Python 中从头实现基线机器学习算法。

完成本教程后，你将知道：

- 如何实现随机预测算法。
- 如何实现零规则预测算法。

让我们开始吧。

### 5.1 描述

有很多机器学习算法可供选择。事实上有数百种。你必须知道给定算法的预测是好是坏。但你怎么知道呢？答案是使用基线预测算法。基线预测算法提供一组预测，你可以像评估问题的任何其他预测一样来评估它们，例如分类准确率或 RMSE。

这些算法的得分在评估问题上的所有其他机器学习算法时提供了所需的比较点。一旦建立，你可以评论给定算法相比于天真基线算法好多少，从而提供关于给定方法实际上有多好的背景。最常用的两个基线算法是：

- 随机预测算法。
- 零规则算法。

当着手解决比传统分类或回归问题更困难的新问题时，首先针对你的预测问题制定一个特定的随机预测算法是个好主意。之后你可以在此基础上改进，并制定一个零规则算法。让我们实现这些算法并看看它们如何工作。

### 5.2 教程

本教程分为 2 部分：

- 随机预测算法。
- 零规则算法。

这些步骤将为你提供实现和计算机器学习算法基线性能所需的基础。

### 5.2.1 随机预测算法

随机预测算法预测训练数据中观察到的随机结果。它可能是实现起来最简单的算法。它要求你存储训练数据中的所有不同结果值，在回归问题上如果有大量不同值，这可能会很大。

因为使用随机数来做决策，所以在使用算法之前修复随机数种子是个好主意。这是为了确保每次运行算法时都能得到同一组随机数，进而得到相同的决策。下面是一个名为 `random_algorithm()` 的函数中随机预测算法的实现。该函数既接受包含输出值的训练数据集，也接受需要预测输出值的测试数据集。该函数适用于分类和回归问题。它假设训练数据中的输出值是每行的最后一列。

首先，从训练数据中收集唯一输出值的集合。然后，为测试集中的每一行从集合中随机选择一个输出值。

```python
# Generate random predictions
def random_algorithm(train, test):
    output_values = [row[-1] for row in train]
    unique = list(set(output_values))
    predicted = list()
    for row in test:
        index = randrange(len(unique))
        predicted.append(unique[index])
    return predicted
```

清单 5.1：生成随机预测的函数。

为了简单起见，我们可以用一个只包含输出列的小数据集来测试这个函数。训练数据集中的输出值要么是 0 要么是 1，这意味着算法将从中选择的预测集是 (0, 1)。测试集也包含单列，没有数据，因为预测未知。

```python
# Example of Making Random Predictions
from random import seed
from random import randrange

# Generate random predictions
def random_algorithm(train, test):
    output_values = [row[-1] for row in train
```

