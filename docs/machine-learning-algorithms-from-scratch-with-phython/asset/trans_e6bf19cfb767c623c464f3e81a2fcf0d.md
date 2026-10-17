

## 5.2 教程

```
unique = list(set(output_values))
predicted = list()
for _ in test:
    index = randrange(len(unique))
    predicted.append(unique[index])
return predicted

seed(1)
train = [[0], [1], [0], [1], [0], [1]]
test = [[None], [None], [None], [None]]
predictions = random_algorithm(train, test)
print(predictions)
```

### 列表 5.2: 进行随机预测的示例。

运行该示例会为测试数据集计算随机预测并打印这些预测。

```
[0, 1, 1, 0]
```

### 列表 5.3: 进行随机预测的示例输出。

随机预测算法易于实现且运行速度快，但作为基准我们可以做得更好。

## 5.2.2 零规则算法

零规则算法比随机算法更好的基准。它使用关于给定问题的更多信息来创建一条规则以进行预测。此规则取决于问题类型。让我们从分类问题开始，预测类标签。

### 分类

对于分类问题，唯一的规则是预测训练数据集中最常见的类值。这意味着如果训练数据集有90个类0的实例和10个类1的实例，它将预测0并达到90/100或90%的基准准确率。

这比随机预测算法好得多，后者平均只能达到82%的准确率。关于如何计算此随机搜索估计值的详细信息，请参见下方：

```
= ((0.9 x 0.9) + (0.1 x 0.1)) x 100
= 82%
(5.1)
```

下面是一个名为 zero_rule_algorithm_classification() 的函数，它针对分类情况实现了此功能。

```
# zero rule algorithm for classification
def zero_rule_algorithm_classification(train, test):
    output_values = [row[-1] for row in train]
    prediction = max(set(output_values), key=output_values.count)
    predicted = [prediction for i in range(len(test))]
    return predicted
```

### 列表 5.4: 生成零规则分类预测的函数。

该函数使用带有 key 属性的 max() 函数，这有点巧妙。给定训练数据中观察到的类值列表，max() 函数获取一组唯一的类值，并对集合中每个类值的类值列表调用 count。结果是，它返回在训练数据集中观察到的类值列表中具有最高观察值计数的类值。

如果所有类值的计数相同，则我们将选择数据集中观察到的第一个类值。一旦选择一个类值，它将用于对测试数据集中的每一行进行预测。下面是一个使用包含4个类0示例和2个类1示例的构造数据集的示例。我们期望算法为测试数据集中的每一行选择类值0作为预测。

```
# Example of Zero Rule Classification Predictions
from random import seed

# zero rule algorithm for classification
def zero_rule_algorithm_classification(train, test):
    output_values = [row[-1] for row in train]
    prediction = max(set(output_values), key=output_values.count)
    predicted = [prediction for i in range(len(test))]
    return predicted

seed(1)
train = [['0'], ['0'], ['0'], ['0'], ['1'], ['1']]
test = [[None], [None], [None], [None]]
predictions = zero_rule_algorithm_classification(train, test)
print(predictions)
```

### 列表 5.5: 零规则分类预测的示例。

运行此示例会生成预测并将其打印到屏幕上。如预期，类值0被选中并预测。

```
['0', '0', '0', '0']
```

### 列表 5.6: 生成零规则分类预测的示例输出。

### 回归

回归问题需要预测实数值。对实数值的良好默认预测是预测中心趋势。这可能是均值或中位数。良好的默认做法是使用训练数据中观察到的输出值的均值（也称为平均值）。

这可能比随机预测具有更低的误差，后者将返回任何观察到的输出值。下面是一个名为 zero_rule_algorithm_regression() 的函数，用于执行此操作。它通过计算观察到的输出值的均值来工作。

mean = \frac{\sum_{i=1}^n value_i}{count(values)} (5.2)

计算后，均值随后被预测为训练数据中每一行的值。

```
# zero rule algorithm for regression
def zero_rule_algorithm_regression(train, test):
    output_values = [row[-1] for row in train]
    prediction = sum(output_values) / float(len(output_values))
    predicted = [prediction for i in range(len(test))]
    return predicted
```

### 列表 5.7: 生成零规则回归预测的函数。

可以使用简单示例测试此函数。我们可以构造一个小数据集，其中均值已知为15。

```
10
15
12
15
18
20
mean = (10 + 15 + 12 + 15 + 18 + 20) / 6
mean = 90 / 6
mean = 15
```

### 列表 5.8: 构造的回归数据集和预期均值。

下面是完整示例。我们期望均值15将被预测为测试数据集中每一行的值。

```
# Example of Zero Rule Regression Predictions
from random import seed

# zero rule algorithm for regression
def zero_rule_algorithm_regression(train, test):
    output_values = [row[-1] for row in train]
    prediction = sum(output_values) / float(len(output_values))
    predicted = [prediction for i in range(len(test))]
    return predicted

seed(1)
train = [[10], [15], [12], [15], [18], [20]]
test = [[None], [None], [None], [None]]
predictions = zero_rule_algorithm_regression(train, test)
print(predictions)
```

### 列表 5.9: 零规则回归预测的示例。

运行该示例会计算打印的预测输出值。如预期，均值15被预测为测试数据集中每一行的值。

```
[15.0, 15.0, 15.0, 15.0]
```

### 列表 5.10: 生成零规则回归预测的示例输出。

## 5.3 扩展

下面是一些基准算法的扩展，你可能希望调查并作为本教程的扩展来实现。

- 替代中心趋势，其中预测中位数、众数或其他中心趋势计算，而不是均值。
- 用于时间序列问题的移动平均，其中预测最后n条记录的均值。

## 5.4 回顾

在本教程中，你发现了在机器学习问题上计算性能基准的重要性。

你现在知道：

- 如何为分类和回归问题实现随机预测算法。
- 如何为分类和回归问题实现零规则算法。

## 5.4.1 下一步

本教程结束了关于数据准备的第1部分。接下来，你将开始关于线性算法的第2部分。在下一个教程中，你将发现如何实现一个测试套件以一致地评估预测建模算法。

## 第6章

## 算法测试套件

我们无法知道哪种算法最适合给定问题。因此，我们需要设计一个测试套件，用于评估不同的机器学习算法。在本教程中，你将发现如何在Python中从头开始开发机器学习算法测试套件。完成本教程后，你将知道：

- 如何实现训练-测试算法测试套件。
- 如何实现k折交叉验证算法测试套件。

让我们开始吧。

## 6.1 描述

测试套件提供了一种在数据集上评估机器学习算法的一致方式。它涉及3个要素：

- 用于拆分数据集的重采样方法。
- 要评估的机器学习算法。
- 用于评估预测的性能度量。

加载和准备数据集是使用测试套件之前必须完成的先决步骤。测试套件必须允许评估不同的机器学习算法，同时保持数据集、重采样方法和性能度量不变。在本教程中，我们将使用真实数据集来演示测试套件。

### 6.1.1 皮马印第安人糖尿病数据集

在本教程中，我们将使用皮马印第安人糖尿病数据集。该数据集涉及在5年内预测糖尿病的发病。该问题上的基准性能约为65%。你可以在附录A，第A.4节中了解更多信息。下载数据集并将其保存到当前工作目录中，文件名为 pima-indians-diabetes.csv。

