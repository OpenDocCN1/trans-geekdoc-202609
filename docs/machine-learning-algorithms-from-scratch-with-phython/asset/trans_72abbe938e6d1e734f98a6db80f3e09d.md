

高方差机器学习算法（例如未剪枝决策树）的性能可以通过训练多棵树并取其预测的平均值来提高。结果通常优于单棵决策树。除了性能提升之外，装袋法的另一个好处是，装袋决策树不会对问题产生过拟合。可以继续添加树，直到达到性能峰值。

### 16.1.2 声纳数据集

在本教程中，我们将使用声纳数据集。该数据集涉及水雷和岩石之间的区分。该问题上的基准性能约为 53%。您可以在附录 A 的第 A.5 节中了解更多信息。下载数据集，并将其保存到当前工作目录中，文件名为 sonar.all-data.csv。

## 16.2 教程

本教程分为 2 个部分：

- 自助重采样。
- 声纳案例研究。

这些步骤为您提供了使用决策树实现和应用自助聚合以解决自身预测建模问题所需的基础。

### 16.2.1 自助重采样

让我们先深入理解自助法的工作原理。我们可以通过从数据集中随机选择行并将其添加到新列表中，来创建数据集的新样本。我们可以重复此过程固定次数，或直到新数据集的大小与原始数据集大小的某个比例相匹配。

我们可以通过不移除已选行来允许有放回抽样，以便该行可用于未来的选择。以下是名为 `subsample()` 的函数，它实现了此过程。来自 random 模块的 `randrange()` 函数用于在循环的每次迭代中选择一个随机行索引添加到样本。样本的默认大小是原始数据集的大小。

```
# Create a random subsample from the dataset with replacement
def subsample(dataset, ratio=1.0):
    sample = list()
    n_sample = round(len(dataset) * ratio)
    while len(sample) < n_sample:
        index = randrange(len(dataset))
        sample.append(dataset[index])
    return sample
```

清单 16.1：从数据集中创建子样本的函数。

我们可以使用此函数来估计构造数据集的均值。首先，我们可以创建一个包含 20 行和 1 列（0 到 9 之间的随机数）的数据集并计算均值。然后，我们可以对原始数据集生成自助样本，计算均值，并重复此过程，直到得到一组均值。对这些样本均值取平均，应该能对整个数据集的均值给出一个稳健的估计。

完整示例如下。每个自助样本是原始 20 个观测值数据集（或 2 个观测值）的 10% 样本。然后，我们通过对原始数据集生成 1、10、100 个自助样本，计算它们的均值，并对所有这些估计均值取平均来进行实验。

```python
# Example of subsampling a dataset
from random import seed
from random import randrange

# Create a random subsample from the dataset with replacement
def subsample(dataset, ratio=1.0):
    sample = list()
    n_sample = round(len(dataset) * ratio)
    while len(sample) < n_sample:
        index = randrange(len(dataset))
        sample.append(dataset[index])
    return sample

# Calculate the mean of a list of numbers
def mean(numbers):
    return sum(numbers) / float(len(numbers))

# Test subsampling a dataset
seed(1)
# True mean
dataset = [[randrange(10)] for i in range(20)]
print('True Mean: %.3f' % mean([row[0] for row in dataset]))
# Estimated means
ratio = 0.10
for size in [1, 10, 100]:
    sample_means = list()
    for i in range(size):
        sample = subsample(dataset, ratio)
        sample_mean = mean([row[0] for row in sample])
        sample_means.append(sample_mean)
    print('Samples=%d, Estimated Mean: %.3f' % (size, mean(sample_means)))
```

清单 16.2：对数据集进行子采样的示例。

运行示例将打印我们旨在估计的原始均值。然后，我们可以看到不同数量的自助样本得到的估计均值。可以看到，使用 100 个样本时，我们能够获得均值的良好估计。

```
True Mean: 4.450
Samples=1, Estimated Mean: 4.500
Samples=10, Estimated Mean: 3.300
Samples=100, Estimated Mean: 4.480
```

清单 16.3：对数据集进行子采样的示例输出。

与计算均值不同，我们可以从每个子样本中创建一个模型。接下来，让我们看看如何合并多个自助模型的预测。

### 16.2.2 声纳案例研究

在本节中，我们将把装袋算法应用于声纳数据集。该示例假设数据集的 CSV 副本位于当前工作目录中，文件名为 sonar.all-data.csv。

首先加载数据集，将字符串值转换为数值，并将输出列从字符串转换为 0 到 1 的整数值。这是通过辅助函数 load_csv()、str_column_to_float() 和 str_column_to_int() 来加载和准备数据集实现的。

我们将使用 k 折交叉验证来估计学习模型在未见数据上的性能。这意味着我们将构建和评估 k 个模型，并将性能估计为平均模型误差。将使用分类准确率来评估每个模型。这些行为在辅助函数 cross_validation_split()、accuracy_metric() 和 evaluate_algorithm() 中提供。

我们还将使用一种针对装袋进行了调整的分类和回归树（CART）算法实现，该实现使用第 11 章中的辅助函数，包括 test_split() 用于将数据集拆分为组，gini_index() 用于评估分割点，get_split() 用于寻找最佳分割点，to_terminal()、split() 和 build_tree() 用于创建单棵决策树，predict() 用于使用决策树进行预测，以及前一步中描述的 subsample() 函数用于从训练数据集中创建子样本。

开发了一个名为 bagging_predict() 的新函数，负责使用每棵决策树进行预测，并将预测合并为单个返回值。这是通过从装袋树生成的预测列表中选择最常见的预测来实现的。

最后，开发了一个名为 bagging() 的新函数，负责创建训练数据集的样本，在每个样本上训练一棵决策树，然后使用装袋树列表对测试数据集进行预测。完整示例如下。

```
# Bagging Algorithm on the Sonar dataset
from random import seed
from random import randrange
from csv import reader

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

# Convert string column to integer
def str_column_to_int(dataset, column):
    class_values = [row[column] for row in dataset]
    unique = set(class_values)
    lookup = dict()
    for i, value in enumerate(unique):
        lookup[value] = i
    for row in dataset:
        row[column] = lookup[row[column]]
    return lookup
```

```
# Split a dataset into k folds
def cross_validation_split(dataset, n_folds):
    dataset_split = list()
    dataset_copy = list(dataset)
    fold_size = int(len(dataset) / n_folds)
    for _ in range(n_folds):
        fold = list()
        while len(fold) < fold_size:
            index = randrange(len(dataset_copy))
            fold.append(dataset_copy.pop(index))
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
# Split a dataset based on an attribute and an attribute value
def test_split(index, value, dataset):
    left, right = list(), list()
    for row in dataset:
        if row[index] < value:
            left.append(row)
        else:
```

