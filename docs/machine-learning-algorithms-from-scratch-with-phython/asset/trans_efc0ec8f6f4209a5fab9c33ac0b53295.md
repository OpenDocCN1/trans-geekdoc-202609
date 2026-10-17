

```python
# Calculate covariance between x and y
def covariance(x, mean_x, y, mean_y):
    covar = 0.0
    for i in range(len(x)):
        covar += (x[i] - mean_x) * (y[i] - mean_y)
    return covar

# Calculate the variance of a list of numbers
def variance(values, mean):
    return sum([(x-mean)**2 for x in values])

# Calculate coefficients
def coefficients(dataset):
    x = [row[0] for row in dataset]
    y = [row[1] for row in dataset]
    x_mean, y_mean = mean(x), mean(y)
    b1 = covariance(x, x_mean, y, y_mean) / variance(x, x_mean)
    b0 = y_mean - b1 * x_mean
    return [b0, b1]

# Simple linear regression algorithm
def simple_linear_regression(train, test):
    predictions = list()
    b0, b1 = coefficients(train)
    for row in test:
        yhat = b0 + b1 * row[0]
        predictions.append(yhat)
    return predictions

# Test simple linear regression
dataset = [[1, 1], [2, 3], [4, 3], [3, 2], [5, 5]]
rmse = evaluate_algorithm(dataset, simple_linear_regression)
print('RMSE: %.3f' % (rmse))
```

清单 7.13：在构造数据集上进行简单线性回归的示例。

运行此示例将显示以下输出，该输出首先列出预测值以及这些预测的 RMSE。

```
[1.1999999999999995, 1.9999999999999996, 3.5999999999999996, 2.8, 4.3999999999999995]
RMSE: 0.693
```

清单 7.14：在构造数据集上进行简单线性回归的输出示例。

最后，我们可以将预测值绘制为一条线，并将其与原始数据集进行比较。

![](img/eb4f6b07d6861add2c4caceda6f4837f_68_0.png)

图 7.2：在构造数据集上简单线性回归预测的图示。

### 7.2.5 瑞典汽车保险案例研究

我们现在知道如何实现简单线性回归模型。让我们将其应用于瑞典保险数据集。本节假设你已将数据集下载到文件 `insurance.csv`，并且它位于当前工作目录中。我们将在前几步的简单线性回归基础上添加一些便捷函数。

具体来说，有一个名为 `load_csv()` 的函数用于加载 CSV 文件，一个名为 `str_column_to_float()` 的函数用于将加载的数据集转换为数字，一个名为 `train_test_split()` 的函数用于使用训练集和测试集评估算法，一个名为 `rmse_metric()` 的函数用于计算 RMSE，还有一个名为 `evaluate_algorithm()` 的函数用于评估算法。

完整的示例如下。使用 60% 的数据作为训练数据集来准备模型，并在剩余的 40% 上进行预测。

```python
# Example of Simple Linear Regression on the Swedish Insurance Dataset
from random import seed
from random import randrange
from csv import reader
from math import sqrt

# Load a CSV file
def load_csv(filename):
    dataset = list()
    with open(filename, 'r') as file:
        csv_reader = reader(file)
        for row in csv_reader:
            if not row:
                continue
            dataset.append(row)
    return dataset

# Convert string column to float
def str_column_to_float(dataset, column):
    for row in dataset:
        row[column] = float(row[column].strip())

# Split a dataset into a train and test set
def train_test_split(dataset, split):
    train = list()
    train_size = split * len(dataset)
    dataset_copy = list(dataset)
    while len(train) < train_size:
        index = randrange(len(dataset_copy))
        train.append(dataset_copy.pop(index))
    return train, dataset_copy

# Calculate root mean squared error
def rmse_metric(actual, predicted):
    sum_error = 0.0
    for i in range(len(actual)):
        prediction_error = predicted[i] - actual[i]
        sum_error += (prediction_error ** 2)
    mean_error = sum_error / float(len(actual))
    return sqrt(mean_error)

# Evaluate an algorithm using a train/test split
def evaluate_algorithm(dataset, algorithm, split, *args):
    train, test = train_test_split(dataset, split)
    test_set = list()
    for row in test:
        row_copy = list(row)
        row_copy[-1] = None
        test_set.append(row_copy)
    predicted = algorithm(train, test_set, *args)
    actual = [row[-1] for row in test]
    rmse = rmse_metric(actual, predicted)
    return rmse

# Calculate the mean value of a list of numbers
def mean(values):
    return sum(values) / float(len(values))

# Calculate covariance between x and y
def covariance(x, mean_x, y, mean_y):
    covar = 0.0
    for i in range(len(x)):
        covar += (x[i] - mean_x) * (y[i] - mean_y)
    return covar

# Calculate the variance of a list of numbers
def variance(values, mean):
    return sum([(x-mean)**2 for x in values])

# Calculate coefficients
def coefficients(dataset):
    x = [row[0] for row in dataset]
    y = [row[1] for row in dataset]
    x_mean, y_mean = mean(x), mean(y)
    b1 = covariance(x, x_mean, y, y_mean) / variance(x, x_mean)
    b0 = y_mean - b1 * x_mean
    return [b0, b1]

# Simple linear regression algorithm
def simple_linear_regression(train, test):
    predictions = list()
    b0, b1 = coefficients(train)
    for row in test:
        yhat = b0 + b1 * row[0]
        predictions.append(yhat)
    return predictions

# Simple linear regression on insurance dataset
seed(1)
# load and prepare data
filename = 'insurance.csv'
dataset = load_csv(filename)
for i in range(len(dataset[0])):
    str_column_to_float(dataset, i)
# evaluate algorithm
split = 0.6
rmse = evaluate_algorithm(dataset, simple_linear_regression, split)
print('RMSE: %.3f' % (rmse))
```

清单 7.15：在保险数据集上进行简单线性回归的示例。

运行该算法会打印训练模型在训练数据集上的 RMSE。得到的分数约为 38（千瑞典克朗），这比同一问题上的基线性能 72（千瑞典克朗）要好得多。

```
RMSE: 38.339
```

清单 7.16：在保险数据集上简单线性回归的输出示例。

### 7.3 扩展

本教程的最佳扩展是在更多问题上尝试该算法。仅包含输入（x）和输出（y）列的小型数据集在统计书籍和课程中常用于演示。许多这类数据集都可以在线获取。寻找更多小型数据集，并使用简单线性回归进行预测。

### 7.4 总结

在本教程中，你了解了如何用 Python 从零开始实现简单线性回归算法。具体来说，你学到了：

- 如何从训练数据集中估计均值、方差和协方差等统计量。
- 如何估计模型系数并使用它们进行预测。
- 如何使用简单线性回归在真实数据集上进行预测。

#### 7.4.1 延伸阅读

- 第 3.1 节 简单线性回归，第 61 页，《统计学习导论》，2014 年。http://amzn.to/2eeTyQX
- 第 18.6 节 线性模型的回归与分类，第 717 页，《人工智能：一种现代方法》，2010 年。http://amzn.to/2e31FqP

#### 7.4.2 下一步

在下一个教程中，你将了解如何实现和应用多元线性回归算法。

## 第 8 章：多元线性回归

许多机器学习算法的核心是优化。机器学习算法使用优化算法在给定训练数据集的情况下找到一组良好的模型参数。机器学习中最常用的优化算法是随机梯度下降。在本教程中，你将了解如何用 Python 从零实现随机梯度下降来优化线性回归算法。

完成本教程后，你将了解：

- 如何使用随机梯度下降估计线性回归系数。
- 如何进行多元线性回归预测。
- 如何使用随机梯度下降实现线性回归，以对新数据进行预测。

让我们开始吧。

### 8.1 描述

在本节中，我们将描述线性回归、随机梯度下降技术以及本教程中使用的葡萄酒质量数据集。

#### 8.1.1 多元线性回归

线性回归是一种预测实数值的技术。容易令人困惑的是，这些需要预测实数值的问题被称为回归问题。线性回归是一种使用直线对输入值和输出值之间的关系进行建模的技术。在超过二维的情况下，这条直线可以被视为一个平面或超平面。

预测是通过输入值的组合来预测输出值。每个输入属性（x）都使用系数（b）加权，学习算法的目标是发现一组能够产生良好预测（y）的系数。

$y = b0 + b1 \times x1 + b2 \times x2 + ...$ (8.1)

可以使用随机梯度下降来求解系数。

