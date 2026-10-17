

列表 14.9: 学习率线性衰减测试。

| 轮次 | 有效学习率 |
|-------|-------------------------|
| 0 | 0.3 |
| 1 | 0.27 |
| 2 | 0.24 |
| 3 | 0.21 |
| 4 | 0.18 |
| 5 | 0.15 |
| 6 | 0.12 |
| 7 | 0.09 |
| 8 | 0.06 |
| 9 | 0.03 |

![](img/eb4f6b07d6861add2c4caceda6f4837f_159_0.png)

我们可以将所有这些整合在一起。下面是一个名为 `train_codebooks()` 的函数，它实现了给定训练数据集训练一组码本向量的过程。该函数除了训练数据集外，还接受 3 个额外参数：要创建和训练的码本向量数量、初始学习率以及训练码本向量的轮次数。

你还可以看到，该函数会跟踪每个轮次的平方误差和，并打印一条消息，显示轮次号、有效学习率和平方误差得分。在调试训练函数或特定预测问题的配置时，这很有帮助。你可以看到使用 `random_codebook()` 来初始化码本向量，并使用 `get_best_matching_unit()` 函数来查找每个轮次内每个训练模式的 BMU。

```python
# Train a set of codebook vectors
def train_codebooks(train, n_codebooks, lrate, epochs):
    codebooks = [random_codebook(train) for i in range(n_codebooks)]
    for epoch in range(epochs):
        rate = lrate * (1.0-(epoch/float(epochs)))
        sum_error = 0.0
        for row in train:
            bmu = get_best_matching_unit(codebooks, row)
            for i in range(len(row)-1):
                error = row[i] - bmu[i]
                sum_error += error**2
                if bmu[-1] == row[-1]:
                    bmu[i] += rate * error
                else:
                    bmu[i] -= rate * error
        print('>epoch=%d, lrate=%.3f, error=%.3f' % (epoch, rate, sum_error))
    return codebooks
```

列表 14.10: 训练码本向量种群的函数。

我们可以将此与上面的示例结合起来，为我们的构造数据集学习一组码本向量。下面是完整示例。

```python
# Example of training a set of codebook vectors
from math import sqrt
from random import randrange
from random import seed

# calculate the Euclidean distance between two vectors
def euclidean_distance(row1, row2):
    distance = 0.0
    for i in range(len(row1)-1):
        distance += (row1[i] - row2[i])**2
    return sqrt(distance)

# Locate the best matching unit
def get_best_matching_unit(codebooks, test_row):
    distances = list()
    for codebook in codebooks:
        dist = euclidean_distance(codebook, test_row)
        distances.append((codebook, dist))
    distances.sort(key=lambda tup: tup[1])
    return distances[0][0]

# Create a random codebook vector
def random_codebook(train):
    n_records = len(train)
    n_features = len(train[0])
    codebook = [train[randrange(n_records)][i] for i in range(n_features)]
    return codebook

# Train a set of codebook vectors
def train_codebooks(train, n_codebooks, lrate, epochs):
    codebooks = [random_codebook(train) for i in range(n_codebooks)]
    for epoch in range(epochs):
        rate = lrate * (1.0-(epoch/float(epochs)))
        sum_error = 0.0
        for row in train:
            bmu = get_best_matching_unit(codebooks, row)
            for i in range(len(row)-1):
                error = row[i] - bmu[i]
                sum_error += error**2
                if bmu[-1] == row[-1]:
                    bmu[i] += rate * error
                else:
                    bmu[i] -= rate * error
        print('>epoch=%d, lrate=%.3f, error=%.3f' % (epoch, rate, sum_error))
    return codebooks

# Test the training function
seed(1)
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
learn_rate = 0.3
n_epochs = 10
n_codebooks = 2
codebooks = train_codebooks(dataset, n_codebooks, learn_rate, n_epochs)
print('Codebooks: %s' % codebooks)
```

列表 14.11: 在构造数据集上训练码本向量的示例。

运行此示例将以初始学习率 0.3 训练一组 2 个码本向量，共 10 个轮次。每个轮次的详细信息都会打印出来，并显示从训练数据中学习到的 2 个码本向量集。我们可以看到，学习率的变化符合我们上面对每个轮次所探索的预期。我们还可以看到，每个轮次的平方误差和在训练结束时仍在继续下降，并且可能有机会进一步调整示例以获得更小的误差。

```
>epoch=0, lrate=0.300, error=139.812
>epoch=1, lrate=0.270, error=47.368
>epoch=2, lrate=0.240, error=27.535
>epoch=3, lrate=0.210, error=26.241
>epoch=4, lrate=0.180, error=25.509
>epoch=5, lrate=0.150, error=24.778
>epoch=6, lrate=0.120, error=24.053
>epoch=7, lrate=0.090, error=23.344
>epoch=8, lrate=0.060, error=22.663
>epoch=9, lrate=0.030, error=21.981
Codebooks: [[7.3188612290158614, 1.9696349335193466, 1], [2.4304257696446854,
 2.8396012380964555, 0]]
```

列表 14.12: 训练码本向量的示例输出。

既然我们知道如何训练一组码本向量，让我们看看如何在真实数据集上使用此算法。

## 14.2.4 电离层案例研究

在本节中，我们将把学习向量量化算法应用于电离层数据集。第一步是加载数据集，并将加载的数据转换为可用于欧氏距离计算的数字。为此，我们将使用辅助函数 `load_csv()` 加载文件，使用 `str_column_to_float()` 将字符串数字转换为浮点数，并使用 `str_column_to_int()` 将类列转换为整数值。

我们将使用 *k* 折交叉验证（5 折）来评估该算法。这意味着每个折叠中将有 \(\frac{351}{5}=70.2\) 或略多于 70 条记录。我们将使用辅助函数 `evaluate_algorithm()` 通过交叉验证来评估该算法，并使用 `accuracy_metric()` 来计算预测的准确性。完整示例如下。

```python
# LVQ for the Ionosphere Dataset
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

# Calculate accuracy percentage
def accuracy_metric(actual, predicted):
    correct = 0
    for i in range(len(actual)):
        if actual[i] == predicted[i]:
            correct += 1
    return correct / float(len(actual)) * 100.0

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

# calculate the Euclidean distance between two vectors
def euclidean_distance(row1, row2):
    distance = 0.0
    for i in range(len(row1)-1):
        distance += (row1[i] - row2[i])**2
    return sqrt(distance)

# Locate the best matching unit
def get_best_matching_unit(codebooks, test_row):
    distances = list()
    for codebook in codebooks:
        dist = euclidean_distance(codebook, test_row)
        distances.append((codebook, dist))
    distances.sort(key=lambda tup: tup[1])
    return distances[0][0]

# Make a prediction with codebook vectors
def predict(codebooks, test_row):
    bmu = get_best_matching_unit(codebooks, test_row)
    return bmu[-1]

# Create a random codebook vector
def random_codebook(train):
    n_records = len(train)
    n_features = len(train[0])
    codebook = [train[randrange(n_records)][i] for i in range(n_features)]
```

