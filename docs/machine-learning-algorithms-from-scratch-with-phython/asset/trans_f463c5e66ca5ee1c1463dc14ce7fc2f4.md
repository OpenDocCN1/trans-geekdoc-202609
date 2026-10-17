

导致每组中出现 50/50 类别分布的分割，其 Gini 分数为 0.5（针对二分类问题）。

通过示例来演示计算 Gini 最为直观。我们有两组数据，每组包含 2 行。第一组中的所有行都属于类别 0，第二组中的所有行都属于类别 1，因此这是一个完美的分割。我们首先需要计算每组中各类别的比例。

```
proportion = \frac{count(class\_value)}{count(rows)}
```

本示例中的比例如下：

```
group\_1\_class\_0 = \frac{2}{2} = 1
group\_1\_class\_1 = \frac{0}{2} = 0
group\_2\_class\_0 = \frac{0}{2} = 0
group\_2\_class\_1 = \frac{2}{2} = 1
```

然后对每个子节点按如下方式计算 Gini：

```
gini\_index = \sum_{i=1}^{n} (proportion_i \times (1.0 - proportion_i))
= 1 - \sum_{i=1}^{n} proportion_i^2
```

然后必须根据每组的大小（相对于父节点中的所有样本，即当前正在分组的所有样本）对每组的 Gini 索引进行加权。我们可以将此权重添加到组的 Gini 计算中，如下所示：

```
gini\_index = (1 - \sum_{i=1}^{n} proportion_i^2) \times \frac{group\_size}{total\_samples}
```

在本示例中，每组的 Gini 分数计算如下：

```
Gini(group\_1) = (1 - (1 \times 1 + 0 \times 0)) \times \frac{2}{4}
Gini(group\_1) = 0.0 \times 0.5
Gini(group\_1) = 0.0

Gini(group\_2) = (1 - (0 \times 0 + 1 \times 1)) \times \frac{2}{4}
Gini(group\_2) = 0.0 \times 0.5
Gini(group\_2) = 0.0
```

然后将分割点处每个子节点的分数相加，以得到可与其他候选分割点进行比较的分割点最终 Gini 分数。该分割点的 Gini 将计算为 0.0 + 0.0，即完美的 Gini 分数 0.0。

下面是一个名为 `gini_index()` 的函数，用于计算一组组和一组已知类别值的 Gini 索引。可以看到，其中包含一些安全检查，以避免对空组进行除以零的操作。

```python
# Calculate the Gini index for a split dataset
def gini_index(groups, classes):
    # count all samples at split point
    n_instances = float(sum([len(group) for group in groups]))
    # sum weighted Gini index for each group
    gini = 0.0
    for group in groups:
        size = float(len(group))
        # avoid divide by zero
        if size == 0:
            continue
        score = 0.0
        # score the group based on the score for each class
        for class_val in classes:
            p = [row[-1] for row in group].count(class_val) / size
            score += p * p
        # weight the group score by its relative size
        gini += (1.0 - score) * (size / n_instances)
    return gini
```

清单 11.1：计算数据集分割 Gini 索引的函数。

我们可以使用上面的示例来测试此函数。我们还可以针对每组中 50/50 分割的最坏情况进行测试。完整示例如下所示。

```python
# Example of calculating Gini index

# Calculate the Gini index for a split dataset
def gini_index(groups, classes):
    # count all samples at split point
    n_instances = float(sum([len(group) for group in groups]))
    # sum weighted Gini index for each group
    gini = 0.0
    for group in groups:
        size = float(len(group))
        # avoid divide by zero
        if size == 0:
            continue
        score = 0.0
        # score the group based on the score for each class
        for class_val in classes:
            p = [row[-1] for row in group].count(class_val) / size
            score += p * p
        # weight the group score by its relative size
        gini += (1.0 - score) * (size / n_instances)
    return gini

# test Gini values
print(gini_index([[[1, 1], [1, 0]], [[1, 1], [1, 0]]], [0, 1]))
print(gini_index([[[1, 0], [1, 0]], [[1, 1], [1, 1]]], [0, 1]))
```

清单 11.2：在人造数据集上计算 Gini 索引的示例。

运行示例将打印两个 Gini 分数，首先是最坏情况下的 0.5 分数，然后是最佳情况下的 0.0 分数。

```
0.5
0.0
```

清单 11.3：计算 Gini 索引的示例输出。

## 11.2.2 创建分割

分割由数据集中的一个属性和一个值组成。我们可以将其概括为要分割的属性索引以及用于按该属性分割行的值。这只是索引数据行的一个有用简写。创建分割涉及三个部分，第一部分我们已经讨论过，即计算 Gini 分数。其余两个部分是：

- 1. 分割数据集。
- 2. 评估所有分割。

让我们逐一查看。

### 分割数据集

分割数据集是指给定属性索引和该属性的分割值，将数据集分离为两个行列表。一旦拥有这两组，就可以使用上面的 Gini 分数来评估分割的代价。分割数据集涉及遍历每一行，检查属性值是低于还是高于分割值，并分别将其分配给左组或右组。下面是实现此过程的名为 test_split() 的函数。

```python
# Split a dataset based on an attribute and an attribute value
def test_split(index, value, dataset):
    left, right = list(), list()
    for row in dataset:
        if row[index] < value:
            left.append(row)
        else:
            right.append(row)
    return left, right
```

清单 11.4：基于分割点分割数据集的函数。

这很简单。请注意，右组包含索引处的值高于或等于分割值的所有行。

### 评估所有分割

有了上面的 Gini 函数和测试分割函数，我们现在拥有评估分割所需的一切。给定一个数据集，我们必须检查每个属性上的每个值作为候选分割，评估分割的代价，并找到可能的最佳分割。一旦找到最佳分割，就可以将其用作决策树中的一个节点。

这是一种穷举且贪心的算法。我们将使用字典来表示决策树中的节点，因为我们可以按名称存储数据。在选择最佳分割并将其用作树的新节点时，我们将存储所选属性的索引、用于分割的该属性值以及由所选分割点分割的两组数据。

每组数据都是由分割过程分配给左组或右组的那些行组成的小型数据集。你可以想象，在构建决策树的过程中，我们可能会递归地再次分割每组。下面是实现此过程的名为 `get_split()` 的函数。可以看到，它遍历每个属性（类别值除外），然后遍历该属性的每个值，在过程中分割和评估分割。在所有检查完成后，将记录最佳分割并返回。

```python
# Select the best split point for a dataset
def get_split(dataset):
    class_values = list(set(row[-1] for row in dataset))
    b_index, b_value, b_score, b_groups = 999, 999, 999, None
    for index in range(len(dataset[0])-1):
        for row in dataset:
            groups = test_split(index, row[index], dataset)
            gini = gini_index(groups, class_values)
            if gini < b_score:
                b_index, b_value, b_score, b_groups = index, row[index], gini, groups
    return {'index':b_index, 'value':b_value, 'groups':b_groups}
```

清单 11.5：在数据集中查找最佳分割点的函数。

我们可以构造一个小数据集来测试此函数和我们的整个数据集分割过程。

| X1 | X2 | Y |
|---|---|---|
| 2.771244718 | 1.784783929 | 0 |
| 1.728571309 | 1.169761413 | 0 |
| 3.678319846 | 2.81281357 | 0 |
| 3.961043357 | 2.61995032 | 0 |
| 2.999208922 | 2.209014212 | 0 |
| 7.497545867 | 3.162953546 | 1 |
| 9.00220326 | 3.339047188 | 1 |
| 7.444542326 | 0.476683375 | 1 |
| 10.12493903 | 3.234550982 | 1 |
| 6.642287351 | 3.319983761 | 1 |

清单 11.6：用于测试 CART 的小型人造数据集。

我们可以使用每个类别的单独颜色来绘制此数据集。可以看到，手动选择 X1（图表中的 x 轴）的一个值来分割此数据集并不困难。

