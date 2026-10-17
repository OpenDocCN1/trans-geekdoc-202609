
yhat 预测值是一个介于 0 和 1 之间的实数值，需要四舍五入为整数值，并映射到预测的类别值。

输入数据中的每一列都有一个关联的 b 系数（一个常数实值），该系数必须从训练数据中学习得到。你想在内存或文件中存储的模型的实际表示是方程中的系数（beta 值或 b）。逻辑回归算法的系数必须从训练数据中估计出来。

### 9.1.2 随机梯度下降

逻辑回归使用梯度下降来更新系数。梯度下降已在第 8.1.2 节中介绍和描述。每次梯度下降迭代中，机器学习语言中的系数（b）使用以下方程更新：

$b = b + \text{learning rate} \times (y - yhat) \times yhat \times (1 - yhat) \times x$ (9.3)

其中 b 是被优化的系数或权重，learning rate 是必须配置的学习率（例如 0.01），(y - yhat) 是训练数据上归因于该权重的模型预测误差，yhat 是系数做出的预测，x 是输入值。

### 9.1.3 皮马印第安人糖尿病数据集

在本教程中，我们将使用皮马印第安人糖尿病数据集。该数据集涉及预测 5 年内糖尿病的发病情况。该问题的基线性能约为 65%。你可以在附录 A 的第 A.4 节了解更多信息。下载数据集并将其以文件名 pima-indians-diabetes.csv 保存到当前工作目录。

## 9.2 教程

本教程分为 3 个部分。

- 1. 进行预测。
- 2. 估计系数。
- 3. 皮马印第安人糖尿病案例研究。

这将为你所需的在预测建模问题中实现和应用随机梯度下降逻辑回归提供基础。

### 9.2.1 进行预测

第一步是开发一个能进行预测的函数。在随机梯度下降中评估候选系数值时，以及在模型最终确定后我们希望开始对测试数据或新数据进行预测时，都需要这个函数。下面是一个名为 `predict()` 的函数，它根据一组系数预测一行的输出值。第一个系数始终是截距，也称为偏差或 b0，因为它是独立的，不负责特定的输入值。

```python
# Make a prediction with coefficients
def predict(row, coefficients):
    yhat = coefficients[0]
    for i in range(len(row)-1):
        yhat += coefficients[i + 1] * row[i]
    return 1.0 / (1.0 + exp(-yhat))
```

清单 9.1：用系数进行逻辑回归预测的函数。

我们可以构造一个小数据集来测试我们的 `predict()` 函数。

| X1 | X2 | Y |
|---|---|---|
| 2.7810836 | 2.550537003 | 0 |
| 1.465489372 | 2.362125076 | 0 |
| 3.396561688 | 4.400293529 | 0 |
| 1.38807019 | 1.850220317 | 0 |
| 3.06407232 | 3.005305973 | 0 |
| 7.627531214 | 2.759262235 | 1 |
| 5.332441248 | 2.088626775 | 1 |
| 6.922596716 | 1.77106367 | 1 |
| 8.675418651 | -0.242068655 | 1 |
| 7.673756466 | 3.508563011 | 1 |

清单 9.2：用于测试逻辑回归的小型构造数据集。

下面是该数据集的绘图，使用不同颜色显示每个点的不同类别。

![](img/eb4f6b07d6861add2c4caceda6f4837f_84_0.png)

图 9.1：用于测试逻辑回归的小型构造数据集的绘图。

我们还可以使用先前准备好的系数来对这个数据集进行预测。综合以上所有内容，我们可以在下面测试我们的 `predict()` 函数。

```python
# Example of making a prediction
from math import exp

# Make a prediction with coefficients
def predict(row, coefficients):
    yhat = coefficients[0]
    for i in range(len(row)-1):
        yhat += coefficients[i + 1] * row[i]
    return 1.0 / (1.0 + exp(-yhat))

# test predictions
dataset = [[2.7810836,2.550537003,0],
[1.465489372,2.362125076,0],
[3.396561688,4.400293529,0],
[1.38807019,1.850220317,0],
[3.06407232,3.005305973,0],
[7.627531214,2.759262235,1],
[5.332441248,2.088626775,1],
[6.922596716,1.77106367,1],
[8.675418651,-0.242068655,1],
[7.673756466,3.508563011,1]]
coef = [-0.406605464, 0.852573316, -1.104746259]
for row in dataset:
    yhat = predict(row, coef)
    print("Expected=%.3f, Predicted=%.3f [%d]" % (row[-1], yhat, round(yhat)))
```

清单 9.3：在构造数据集上进行预测的示例。

有两个输入值（X1 和 X2）和三个系数值（b0、b1 和 b2）。我们为这个问题建模的预测方程是：

\( y = \frac{1.0}{1.0 + e^{-(b0+b1\times X1+b2\times X2)}} \) (9.4)

或者，使用我们手工选择的特定系数值：

\( y = \frac{1.0}{1.0 + e^{-(-0.406605464+0.852573316\times X1+-1.104746259\times X2)}} \) (9.5)

运行该函数，我们得到的预测与预期输出（y）值相当接近，并且四舍五入后可以对类别做出正确的预测。

```
Expected=0.000, Predicted=0.299 [0]
Expected=0.000, Predicted=0.146 [0]
Expected=0.000, Predicted=0.085 [0]
Expected=0.000, Predicted=0.220 [0]
Expected=0.000, Predicted=0.247 [0]
Expected=1.000, Predicted=0.955 [1]
Expected=1.000, Predicted=0.862 [1]
Expected=1.000, Predicted=0.972 [1]
Expected=1.000, Predicted=0.999 [1]
Expected=1.000, Predicted=0.905 [1]
```

清单 9.4：在构造数据集上进行预测的示例输出。

现在，我们准备实现随机梯度下降来优化系数值。

你可以看到，此外我们每个 epoch 都会跟踪平方误差之和（一个正值），以便在每个外层循环打印出一条友好的消息。我们可以在上面同一个小型构造数据集上测试这个函数。

```python
# Example of estimating coefficients
from math import exp

# Make a prediction with coefficients
def predict(row, coefficients):
    yhat = coefficients[0]
    for i in range(len(row)-1):
        yhat += coefficients[i + 1] * row[i]
    return 1.0 / (1.0 + exp(-yhat))

# Estimate logistic regression coefficients using stochastic gradient descent
def coefficients_sgd(train, l_rate, n_epoch):
    coef = [0.0 for i in range(len(train[0]))]
    for epoch in range(n_epoch):
        sum_error = 0
        for row in train:
            yhat = predict(row, coef)
            error = row[-1] - yhat
            sum_error += error**2
            coef[0] = coef[0] + l_rate * error * yhat * (1.0 - yhat)
            for i in range(len(row)-1):
                coef[i + 1] = coef[i + 1] + l_rate * error * yhat * (1.0 - yhat) * row[i]
        print('>epoch=%d, lrate=%.3f, error=%.3f' % (epoch, l_rate, sum_error))
    return coef

# Calculate coefficients
dataset = [[2.7810836,2.550537003,0],
    [1.465489372,2.362125076,0],
    [3.396561688,4.400293529,0],
    [1.38807019,1.850220317,0],
    [3.06407232,3.005305973,0],
    [7.627531214,2.759262235,1],
    [5.332441248,2.088626775,1],
    [6.922596716,1.77106367,1],
    [8.675418651,-0.242068655,1],
    [7.673756466,3.508563011,1]]
l_rate = 0.3
n_epoch = 100
coef = coefficients_sgd(dataset, l_rate, n_epoch)
print(coef)
```

清单 9.6：在构造数据集上估计系数的示例。

我们使用较大的学习率 0.3，并训练模型 100 个 epoch，即系数对整个训练数据集的 100 次暴露。运行该示例会在每个 epoch 打印一条消息，包含该 epoch 的平方误差和，以及最终的系数集。

```
...
>epoch=95, lrate=0.300, error=0.023
>epoch=96, lrate=0.300, error=0.023
>epoch=97, lrate=0.300, error=0.023
>epoch=98, lrate=0.300, error=0.023
>epoch=99, lrate=0.300, error=0.022
[-0.8596443546618897, 1.5223825112460005, -2.218700210565016]
```

清单 9.7：在构造数据集上估计系数的示例输出。

你可以看到即使在最后一个 epoch，误差仍然在下降。我们可能可以训练更长时间（更多 epoch）或增加每个 epoch 更新系数的量（更高的学习率）。不妨试验一下，看看你能得到什么结果。现在，让我们将此算法应用于真实数据集。

### 9.2.3 皮马印第安人糖尿病案例研究

在本节中，我们将在糖尿病数据集上使用随机梯度下降训练一个逻辑回归模型。该示例假设数据集的 CSV 副本位于当前工作目录，文件名为 pima-indians-diabetes.csv。

首先加载数据集，将字符串值转换为数值，并将每一列归一化到 0 到 1 的范围内。这是通过辅助函数 `load_csv()` 和 `str_column_to_float()` 来加载和准备数据集，以及 `dataset_minmax()` 和 `normalize_dataset()` 来实现归一化。

我们将使用 k 折交叉验证来估计学习模型在未见数据上的表现。这意味着我们将构建并评估 k 个模型，并将性能估计为平均模型性能。分类准确率将用于评估每个模型。这些行为由 `cross_validation_split()`、`accuracy_metric()` 和 `evaluate_algorithm()` 辅助函数提供。

我们将使用上面创建的 `predict()` 和 `coefficients_sgd()` 函数，以及一个新的 `logistic_regression()` 函数来训练模型。下面是完整的示例。

```python
# Logistic Regression on Diabetes Dataset
from random import seed
from random import randrange
from csv import reader
from math import exp

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

# Find the min and max values for each column
def dataset_minmax(dataset):
    minmax = list()
    for i in range(len(dataset[0])):
```

