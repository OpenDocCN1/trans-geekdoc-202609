
dataset_split.append(fold)
return dataset_split
```

```
# Calculate accuracy percentage
def accuracy_metric(actual, predicted):
    correct = 0
    for i in range(len(actual)):
        if actual[i] == predicted[i]:
            correct += 1
    return correct / float(len(actual)) * 100.0
```

```
# Evaluate an algorithm using a cross validation split
def evaluate_algorithm(dataset, algorithm, n_folds, *args):
    folds = cross_validation_split(dataset, n_folds)
    scores = list()
    for fold in folds:
        train_set = list(folds)
        train_set.remove(fold)
        train_set = sum(train_set, [])
        test_set = list()
        for row in fold:
            row_copy = list(row)
            test_set.append(row_copy)
            row_copy[-1] = None
        predicted = algorithm(train_set, test_set, *args)
        actual = [row[-1] for row in fold]
        accuracy = accuracy_metric(actual, predicted)
        scores.append(accuracy)
    return scores
```

```
# zero rule algorithm for classification
def zero_rule_algorithm_classification(train, test):
    output_values = [row[-1] for row in train]
    prediction = max(set(output_values), key=output_values.count)
    predicted = [prediction for i in range(len(test))]
    return predicted
```

```
# Test cross validation test harness
seed(1)
# load and prepare data
filename = 'pima-indians-diabetes.csv'
dataset = load_csv(filename)
for i in range(len(dataset[0])):
    str_column_to_float(dataset, i)
# evaluate algorithm
n_folds = 5
scores = evaluate_algorithm(dataset, zero_rule_algorithm_classification, n_folds)
print('Scores: %s' % scores)
print('Mean Accuracy: %.3f%%' % (sum(scores)/len(scores)))
```

列表 6.5: 糖尿病数据集上 k 折交叉验证算法测试框架示例。

共使用了 5 个交叉验证折叠来评估零规则算法。因此，evaluate_algorithm() 算法返回了 5 个分数。运行此示例既会打印计算出的分数列表，也会打印平均分数。

分数: [60.130718954248366, 62.745098039215684, 64.70588235294117, 71.89542483660131,
66.01307189542483]
平均准确率: 65.098%

列表 6.6: 使用交叉验证测试框架的示例输出。

你现在有两个不同的测试框架可用于评估自己的机器学习算法。

## 6.3 扩展

本节列出了本教程的扩展，你可以考虑。

- **参数化评估**。传入用于评估预测的函数，使你能够无缝处理回归问题。
- **参数化重采样**。传入用于计算重采样分割的函数，使你能够轻松在训练-测试和交叉验证方法之间切换。
- **标准差分数**。计算标准差，以了解使用交叉验证评估算法时分数的离散程度。

## 6.4 回顾

在本教程中，你了解了如何从头开始创建测试框架来评估机器学习算法。具体来说，你现在知道：

- 如何实现和使用训练-测试算法测试框架。
- 如何实现和使用交叉验证算法测试框架。

### 6.4.1 下一节

在下一个教程中，你将了解如何实现和应用简单线性回归算法。

## 第 7 章

## 简单线性回归

线性回归是一种有着 200 多年历史的预测方法。简单线性回归是一个非常适合初学者实现的第一个机器学习算法，因为它要求你从训练数据集中估计属性，但又足够简单，初学者也能理解。在本教程中，你将了解如何在 Python 中从头开始实现简单线性回归算法。

完成本教程后，你将知道：

- 如何从训练数据中估计统计量。
- 如何从数据中估计线性回归系数。
- 如何使用线性回归对新数据进行预测。

让我们开始吧。

## 7.1 描述

本节分为两部分：简单线性回归技术的描述，以及我们稍后将应用该技术的数据集的描述。

### 7.1.1 简单线性回归

线性回归假设输入变量 (X) 与单个输出变量 (y) 之间存在线性或直线关系。更具体地说，输出 (y) 可以通过输入变量 (X) 的线性组合来计算。当只有一个输入变量时，该方法称为简单线性回归。

在简单线性回归中，我们可以使用训练数据上的统计量来估计模型所需的系数，以便对新数据进行预测。简单线性回归模型的直线可以写成：

```
y = b0 + b1 × x
(7.1)
```

其中 b0 和 b1 是我们必须从训练数据中估计的系数。一旦系数已知，我们就可以使用此方程来估计给定新输入示例 x 时的输出值 y。这要求你从数据中计算统计属性，例如均值、方差和协方差。

所有代数推导都已处理完毕，我们只需实现一些算术运算来估计简单线性回归系数。简而言之，我们可以按如下方式估计系数：

\(B1 = \frac{\sum_{i=1}^n ((x_i - mean(x)) \times (y_i - mean(y)))}{\sum_{i=1}^n (x_i - mean(x))^2}\)
\(B0 = mean(y) - B1 \times mean(x)\)

其中 i 指的是输入 x 或输出 y 的第 i 个值。如果现在还不清楚，不要担心，这些是我们将在本教程中实现的函数。

### 7.1.2 瑞典汽车保险数据集

在本教程中，我们将使用瑞典汽车保险数据集。该数据集涉及总索赔支付的预测。该问题的基准 RMSE 约为 72.251 千克朗。你可以在附录 A 第 A.2 节中了解更多信息。下载数据集并将其保存到当前工作目录中，文件名为 insurance.csv。注意：你可能需要将欧洲逗号 (,) 转换为小数点 (.)。你还需要将文件从空格分隔的变量更改为 CSV 格式。

## 7.2 教程

本教程分为五个部分：

- 1. 计算均值和方差。
- 2. 计算协方差。
- 3. 估计系数。
- 4. 进行预测。
- 5. 瑞典汽车保险案例研究。

这些步骤将为你实现和训练用于自身预测问题的简单线性回归模型奠定基础。

### 7.2.1 计算均值和方差

第一步是从训练数据中估计输入和输出变量的均值和方差。一组数字的均值可以按如下方式计算：

\(mean(x) = \frac{\sum_{i=1}^n x_i}{count(x)}\)

下面是一个名为 mean() 的函数，它为一组数字实现此行为。

```python
# Calculate the mean value of a list of numbers
def mean(values):
    return sum(values) / float(len(values))
```

列表 7.1: 计算一组数字均值的函数。

方差是每个值与均值之差的平方和。一组数字的方差可以按如下方式计算：

variance = \sum_{i=1}^n (x_i - mean(x))^2 (7.4)

下面是一个名为 variance() 的函数，用于计算一组数字的方差。它要求将列表的均值作为参数提供，这样我们就不需要多次计算它。

```python
# Calculate the variance of a list of numbers
def variance(values, mean):
    return sum([(x-mean)**2 for x in values])
```

列表 7.2: 计算一组数字方差的函数。

我们可以将这两个函数放在一起，并在一个小的构造数据集上对其进行测试。下面是一个 x 和 y 值的小数据集。

| x | y |
|---|---|
| 1 | 1 |
| 2 | 3 |
| 4 | 3 |
| 3 | 2 |
| 5 | 5 |

列表 7.3: 用于测试的小型构造数据集。

我们可以按如下方式将此数据集绘制在散点图上：

![](img/eb4f6b07d6861add2c4caceda6f4837f_62_0.png)

图 7.1: 小型构造数据集的图表。
