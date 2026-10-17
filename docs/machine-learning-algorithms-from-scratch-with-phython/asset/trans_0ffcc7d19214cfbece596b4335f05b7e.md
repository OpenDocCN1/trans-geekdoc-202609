
图11.1：用于测试CART的小型人工数据集图。

下面的示例将所有内容整合在一起。

```python
# Example of getting the best split

# Split a dataset based on an attribute and an attribute value
def test_split(index, value, dataset):
    left, right = list(), list()
    for row in dataset:
        if row[index] < value:
            left.append(row)
        else:
            right.append(row)
    return left, right

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

# Select the best split point for a dataset
def get_split(dataset):
    class_values = list(set(row[-1] for row in dataset))
    b_index, b_value, b_score, b_groups = 999, 999, 999, None
    for index in range(len(dataset[0])-1):
        for row in dataset:
            groups = test_split(index, row[index], dataset)
            gini = gini_index(groups, class_values)
            print('X%d < %.3f Gini=%.3f ' % ((index+1), row[index], gini))
            if gini < b_score:
                b_index, b_value, b_score, b_groups = index, row[index], gini, groups
    return {'index':b_index, 'value':b_value, 'groups':b_groups}

# Test getting the best split
dataset = [[2.771244718,1.784783929,0],
    [1.728571309,1.169761413,0],
    [3.678319846,2.81281357,0],
    [3.961043357,2.61995032,0],
    [2.999208922,2.209014212,0],
    [7.497545867,3.162953546,1],
    [9.00220326,3.339047188,1],
    [7.444542326,0.476683375,1],
    [10.12493903,3.234550982,1],
    [6.642287351,3.319983761,1]]
split = get_split(dataset)
print('Split: [X%d < %.3f]' % ((split['index']+1), split['value']))
```

清单11.7：计算人工数据集上最佳分割的示例。

`get_split()`函数已被修改，以便在评估时打印每个分割点及其基尼指数。运行该示例会打印所有基尼分数，然后打印数据集中最佳分割的分数：X1 < 6.642，基尼指数为0.0，即完美分割。

```
X1 < 2.771 Gini=0.444
X1 < 1.729 Gini=0.500
X1 < 3.678 Gini=0.286
X1 < 3.961 Gini=0.167
X1 < 2.999 Gini=0.375
X1 < 7.498 Gini=0.286
X1 < 9.002 Gini=0.375
X1 < 7.445 Gini=0.167
X1 < 10.125 Gini=0.444
X1 < 6.642 Gini=0.000
X2 < 1.785 Gini=0.500
X2 < 1.170 Gini=0.444
X2 < 2.813 Gini=0.320
X2 < 2.620 Gini=0.417
X2 < 2.209 Gini=0.476
X2 < 3.163 Gini=0.167
X2 < 3.339 Gini=0.444
X2 < 0.477 Gini=0.500
X2 < 3.235 Gini=0.286
X2 < 3.320 Gini=0.375
Split: [X1 < 6.642]
```

清单11.8：查找最佳分割的示例输出。

既然我们知道如何在数据集或行列表中找到最佳分割点，让我们看看如何利用它来构建决策树。

## 11.2.3 构建树

创建树的根节点很简单。我们使用整个数据集调用上述的`get_split()`函数。为树添加更多节点则更有趣。构建树可分为三个主要部分：

- 1. 终端节点。
- 2. 递归分割。
- 3. 构建树。

### 终端节点

我们需要决定何时停止树的增长。我们可以使用节点的深度以及训练数据集中该节点负责的行数来判断。

- **最大树深度**。这是从树的根节点算起的最大节点数。一旦达到树的最大深度，我们必须停止添加新节点。更深的树更复杂，更容易过度拟合训练数据。
- **最小节点记录数**。这是给定节点负责的最小训练模式数。一旦达到或低于此最小值，我们必须停止分割和添加新节点。负责过少训练模式的节点预计过于具体，可能过度拟合训练数据。

这两种方法将作为用户指定的参数用于我们的树构建过程。还有一个条件：可能会选择一个分割，使得所有行都属于一个组。在这种情况下，我们将无法继续分割和添加子节点，因为在一侧或另一侧我们没有记录可分割。

现在我们对何时停止树的增长有了一些想法。当我们在某个点停止增长时，该节点被称为终端节点，用于进行最终预测。做法是取分配给该节点的行组，并选择该组中最常见的类别值。这将用于进行预测。下面是一个名为`to_terminal()`的函数，它将为一组行选择一个类别值。它返回一行列表中最常见的输出值。

```python
# Create a terminal node value
def to_terminal(group):
    outcomes = [row[-1] for row in group]
    return max(set(outcomes), key=outcomes.count)
```

清单11.9：创建终端节点的函数。

### 递归分割

我们知道如何以及何时创建终端节点；现在我们可以构建树了。构建决策树涉及对为每个节点创建的组反复调用上面开发的`get_split()`函数。添加到现有节点的新节点称为子节点。一个节点可以有零个子节点（终端节点）、一个子节点（一侧直接进行预测）或两个子节点。在给定节点的字典表示中，我们将子节点称为左节点和右节点。

一旦创建了节点，我们就可以通过再次调用相同的函数，对分割产生的每个数据组递归地创建子节点。下面是一个实现此递归过程的函数。它以节点以及最大深度、节点中的最小模式数和节点的当前深度作为参数。你可以想象第一次调用时传入根节点和深度1的情况。此函数最好分步骤说明：

- 首先，提取由该节点分割的两组数据供使用，并将其从节点中删除。当我们在这些组上操作时，节点不再需要访问这些数据。
- 接下来，我们检查左行组或右行组是否为空，如果为空，则使用现有的记录创建一个终端节点。
- 然后我们检查是否已达到最大深度，如果是，则创建一个终端节点。
- 然后我们处理左子节点：如果行组太小，则创建终端节点；否则以深度优先的方式创建并添加左节点，直到该分支达到树的底部。
- 然后以同样的方式处理右侧，同时我们沿构建好的树返回根节点。

```python
# Create child splits for a node or make terminal
def split(node, max_depth, min_size, depth):
    left, right = node['groups']
    del(node['groups'])
    # check for a no split
    if not left or not right:
        node['left'] = node['right'] = to_terminal(left + right)
        return
    # check for max depth
    if depth >= max_depth:
        node['left'], node['right'] = to_terminal(left), to_terminal(right)
        return
    # process left child
    if len(left) <= min_size:
        node['left'] = to_terminal(left)
    else:
        node['left'] = get_split(left)
        split(node['left'], max_depth, min_size, depth+1)
    # process right child
    if len(right) <= min_size:
        node['right'] = to_terminal(right)
    else:
        node['right'] = get_split(right)
        split(node['right'], max_depth, min_size, depth+1)
```

清单11.10：递归创建分割点的函数。

### 构建树

现在我们可以将所有部分组合在一起。构建树涉及创建根节点，然后调用`split()`函数，该函数随后递归调用自身以构建整棵树。下面是实现此过程的小型`build_tree()`函数。

```python
# Build a decision tree
def build_tree(train, max_depth, min_size):
    root = get_split(train)
    split(root, max_depth, min_size, 1)
    return root
```

清单11.11：创建决策树的函数。

我们可以使用上面构造的小型数据集来测试整个流程。下面是完整的示例。此外还包含一个小的`print_tree()`函数，它递归地打印决策树的节点，每个节点一行。虽然不像真正的决策树图那样醒目，但它可以让你了解树的结构和整个过程中所做的决策。

```python
# Example of building a tree

# Split a dataset based on an attribute and an attribute value
def test_split(index, value, dataset):
    left, right = list(), list()
    for row in dataset:
        if row[index] < value:
            left.append(row)
        else:
            right.append(row)
    return left, right

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

