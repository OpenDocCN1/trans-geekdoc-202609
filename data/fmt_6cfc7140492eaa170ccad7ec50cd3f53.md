
```python
[['E001', 'Partha', 'Director', 'Married', 2],
['E002', 'Deepshree', 'Manager', 'Married', 2],
['E003', 'Riya', 'Programmer', 'Single', 0],
['E004', 'Rano', 'Programmer', 'Single', 0],
['E005', 'Ujwala', 'Programmer', 'Widow', 1],
['E006', 'Anita', 'Manager', 'Married', 1],
['E007', 'Nomita', 'Programmer', 'Divorceee', 2],
['E008', 'Anil', 'Programmer', 'Widower', 0],
['E009', 'Amarendra', 'Programmer', 'Married', 1],
['E010', 'Anuj', 'Manager', 'Married', 2]]
```

我们为这些数据创建一个 dataframe，如下所示：

```python
import pandas as pd

df = pd.DataFrame(data, columns=['EmployeeID', 'Name', 'Designation', 'MaritalStatus', 'NumberOfChildren'])
```

编码器 335

)
`df`

| EmployeeID | 姓名 | 职位 | 婚姻状况 | 数量 |
|---|---|---|---|---|
| 0 | E001 | Partha | Director | Married | 2 |
| 1 | E002 | Deepshree | Manager | Married | 2 |
| 2 | E003 | Riya | Programmer | Single | 0 |
| 3 | E004 | Rano | Programmer | Single | 0 |
| 4 | E005 | Ujwala | Programmer | Widow | 1 |
| 5 | E006 | Anita | Manager | Married | 1 |
| 6 | E007 | Nomita | Programmer | Divorce | 2 |
| 7 | E008 | Anil | Programmer | Widower | 0 |
| 8 | E009 | Amarendra | Programmer | Married | 1 |
| 9 | E010 | Anuj | Manager | Married | 2 |

我们将在`Designation`列上应用独热编码`One-Hot Encoding`：
`from sklearn.preprocessing import OneHotEncoder`

```python
oheDesignation = OneHotEncoder()
transformed = oheDesignation.fit_transform(df['Designation']).todense()
dfTemp = pd.DataFrame(transformed, columns = oheDesignation.get_feature_names_out())
print(dfTemp)
```

Designation_Director Designation_Manager Designation_Programmer

| | 1.0 | 0.0 | 0.0 |
|---|---|---|---|
| 0 | | 0.0 | 0.0 |
| 1 | | 0.0 | 1.0 | 0.0 |
| 2 | | 0.0 | 0.0 | 1.0 |
| 3 | | 0.0 | 0.0 | 1.0 |
| 4 | 0.0 | 0.0 | 1.0 |
| 5 | 0.0 | 1.0 | 0.0 |
| 6 | 0.0 | 0.0 | 1.0 |
| 7 | 0.0 | 0.0 | 1.0 |
| 8 | 0.0 | 0.0 | 1.0 |
| 9 | 0.0 | 1.0 | 0.0 |

# 掌握机器学习分类算法

注意，为`Designation`列中的三个值创建了三列。当我们把这些列添加到原始 dataframe 中时，将得到如下：

```python
df = pd.concat([df, dfTemp], axis=1)
df[['Name', 'Designation', 'Designation_Director', 'Designation_Manager', 'Designation_Programmer']]
```

| 姓名 | 职位 | Designation_Director | Designation_Manager | Designation_Programmer |
|---|---|---|---|---|
| 0 | Partha | 1.0 | 0.0 | 0.0 |
| 1 | Deepshree | Manager | 0.0 | 1.0 | 0.0 |
| 2 | Riya | Programmer | 0.0 | 0.0 | 1.0 |
| 3 | Rano | Programmer | 0.0 | 0.0 | 1.0 |
| 4 | Ujwala | Programmer | 0.0 | 0.0 | 1.0 |
| 5 | Anita | Manager | 0.0 | 1.0 | 0.0 |
| 6 | Nomita | Programmer | 0.0 | 0.0 | 1.0 |
| 7 | Anil | Programmer | 0.0 | 0.0 | 1.0 |
| 8 | Amarendra | Programmer | 0.0 | 0.0 | 1.0 |
| 9 | Anuj | Manager | 0.0 | 1.0 | 0.0 |

注意，对于`Designation`的每一个值，列值中有一个 1，其余值为 0。如果我们使用独热编码，将为数据集带来额外的特征。这些额外特征将等于应用独热编码的列中的唯一值。例如，`Designation`有三个唯一值。因此，我们得到了三个额外的特征。

## 结论

编码器对于将非数值数据转换为数值至关重要。这一步是必要的，因为我们只能用数值数据来创建机器学习模型。我们讨论了两种编码器：标签编码器`Label Encoder`和独热编码器`One-Hot Encoder`。这两个是我们常用的编码器。

其他编码器还包括目标编码器`Target Encoder`、频率/计数编码器`Frequency/Count Encoder`、二进制编码器`Binary Encoder`等。然而，这些很少使用。

# 注意事项

- 当一列具有固定数量的非数值唯一值时，我们使用 `Label Encoder` 将这些非数值值转换为数值。
- `Scikit-Learn` 中的 `Label Encoder` 从 0 开始为唯一标签分配唯一值。
- 如果是为了建模，则我们使用 `One-Hot Encoder`。
- `One-Hot Encoder` 创建的向量包含的元素数量与列中唯一值的数量相同。
  - 创建的向量中的元素只能是 0 和 1。
  - 创建的向量中的元素是与要表示的值相关的元素之一，向量中的所有其他值均为 0。

# 加入我们书籍的 Discord 空间

加入书籍的 Discord 工作空间获取最新更新、全球科技动态、新发布以及与作者的交流：

https://discord.gg/example

![](img/11af2c4c7dddfed06ed0085160c6dfb_357_0.png)

# 附录 8
## 熵

在第 5 章决策树算法中，我们讨论了如何使用 Gini 指数创建决策树。另一种方法是使用熵`Entropy`和信息增`Information Gain`创建决策树。在本附录中，我们将讨论如何使用熵和信息增的概念创建决策树。为了使此讨论与第 5 章决策树算法的讨论相关，我们在本附录中使用与第 5 章相同的示例数据集。

## 结构

在本章中，我们将讨论以下主题：

- 熵
- 信息增
- 使用熵构建决策树
- 使用 `Scikit-Learn` 利用熵构建决策树

# 熵

熵的概念源于物理学。像物理学中一样，熵是环境中随机性的度量。在讨论数据时，这里的熵指的是数据中存在的随机性程度。熵的值可以在 0 到 1 之间。如果一个数据集的熵值为 1，意味着该数据集是完全随机的。如果一个数据集的熵值为 0，则意味着该数据集是纯净的。

计算熵的公式如下：

```
Entropy = -\sum_{i=1}^{n}(p_i \log_2(p_i))
```

这里，`i` 指数据集中唯一类别的数量，从 1 变到 `n`，意味着数据集有 `n` 个类。`p_i` 是数据集中类 `i` 出现的概率。

为了理解，假设一个数据集有两个类，0 和 1。假设该数据集有三个类 0 的元素和七个类 1 的元素。那么 `p_0 = 3/10`，`p_1 = 7/10`。熵的计算为：

`Entropy = -(0.3 \log_2(0.3) + 0.7 \log_2(0.7)) \approx 0.88`

如果数据集只有一个类，例如十个类 0 元素和零个类 1 元素，那么 `p_0 = 10/10 = 1`，`p_1 = 0/10 = 0`。

`Entropy = -(1 \log_2(1) + 0 \log_2(0)) = 0`

# 信息增

回想在决策树中，有一个根节点。在根节点下，有两个或多个节点。这些节点可以是全是叶子节点、决策节点，或者是叶子节点和决策节点的混合。在每个决策节点下，我们可能都有类似的结构。

考虑图 A8.1 中的决策树。在这里，节点 A 是根节点。节点 B 是决策节点。节点 C、D 和 E 是叶子节点。在图 A8.1 中，节点 A 是 B 的父节点，节点 B 是 A 的子节点。

![](img/11af2c4c7dddfed06ed0085160c6dfb_360_0.png)

图 A8.1：用于说明的示例决策树

计算子节点的信息增。

节点的信息增公式如下：

`Information Gain = Entroparent - Entropychild`

假设节点 A 的熵为 0.9，节点 B 的熵为 0.3。那么节点 B 的信息增将为 `(0.9 - 0.3) = 0.6`。

掌握机器学习的分类算法

在第 5 章决策树算法中，我们已经看到尝试了许多可以划分决策树的值。使用吉尼指数`Gini index`，我们考虑在损失`Loss`最小处进行划分。使用熵`Entropy`，我们将在信息增益`Information Gain`最大值处划分决策树。

## 使用熵构建决策树

我们有一个包含 10 条记录的数据集，其中有两个独立变量和一个因变量。设独立变量为 `x_1` 和 `x_2`，因变量为 `y`。参考下表：

| `x_1` | `x_2` | `y` |
|---|---|---|
| 1 | 4 | 0 |
| 7 | 6 | 0 |
| 1 | 6 | 0 |
| 1 | 2 | 1 |
| 5 | 2 | 1 |
| 7 | 2 | 1 |
| 5 | 4 | 0 |
| 2 | 4 | 0 |
| 1 | 7 | 1 |
| 2 | 7 | 1 |

表附录 8.1：原始数据

表附录 8.1 中的数据显示因变量 `y` 有两个值——0 和 1。因此，数据被分为两类——0 和 1。

首先，让我们计算整个数据集的熵。我们看到，类别 0 有 5 个数据点，类别 1 有 5 个数据点。因此，结果如下。

`P_0 = 5/10 = 0.5` 且 `P_1 = 5/10 = 0.5`

使用这些 `P_0` 和 `P_1` 值，我们可以如下计算整个数据集的熵：

```
Entropy = - ((0.5 * log_2(0.5)) + (0.5 * log_2(0.5))) = - ((0.5 * (-1.0)) + (0.5 * (-1.0)) = - (-0.5) + (-0.5)) = - (-1.0) = 1
```

由于整个数据集的熵就是根节点的熵，我们将写为：

`Entropy_root = 1`

为了构建决策树，我们需要对特征 `x_1` 和 `x_2` 尝试不同的点以进行决策划分。因此，我们计算 `x_1` 和 `x_2` 可能出现划分的数值。我们将通过表 A8.1 中的数据来理解这一概念。

为了计算 `x_1` 的差异，我们考虑从 `x_1` 最小值到最大值的范围。然后，我们在该范围内按间隔取点。`minimum(x_1) = 1` 且 `maximum(x_1) = 7`。为了避免边界情况，我们将范围的上限考虑 `maximum(x_1) + 1`。因此，`x_1` 的范围是 1 到 8。我们将在该范围内考虑 0.5 的间隔。因此，我们尝试用于划分决策的 `x_1` 值如下：

1. 1.00, 2.50, 3.00, 3.50, 4.50, 5.00, 5.50, 6.00, 6.50, 6.00, 7.00, 7.50

同样，我们考虑变量 `x_2` 用于划分决策。`minimum(x_2) = 2` 且 `maximum(x_2) = 7`。因此，`x_2` 的范围是 2 到 8。我们尝试用于划分决策的 `x_2` 值如下。

2.00, 2.50, 3.00, 3.50, 4.00, 5.00, 5.50, 6.00, 6.50, 7.00, 7.50

我们用于划分决策树的点被称为**阈值`thresholds`**。

让我们计算阈值 `x_1 = 1.00` 的熵。因此，我们根据 `x_1 <= 1.00` 划分数据集，划分左侧的数据集和右侧的数据集如表附录 8.2 所示：

| `x_1 <= 1.00` | | | `x_1 > 1.00` | | |
|---|---|---|---|---|---|
| `x_1` | `x_2` | `y` | `x_1` | `x_2` | `y` |
| 1 | 4 | | 2 | 4 | 0 |
| 1 | 6 | 0 | 2 | 7 | 1 |
| 1 | 2 | 1 | 5 | 2 | 1 |
| 1 | 7 | 1 | 5 | 4 | 0 |
| | | | 7 | 2 | 1 |
| | | | 7 | 6 | 0 |

*表附录 8.2：`x_1 <= 1.00` 的左、右数据集*

从表附录 8.2 中我们得到划分左侧有 4 个数据点，右侧有 6 个数据点。我们计算左侧数据集和右侧数据集的熵。

计算左侧数据集的熵如下：

```
p_0 = 2/4 = 0.5 且 p_1 = 2/4 = 0.5
```

使用这些 `p_0` 和 `p_1` 值，我们计算左侧数据集的熵：

```
Entropyleft = - ((0.5 * log_2(0.5)) + (0.5 * log_2(0.5))) = - ((0.5 * (-1.0)) + (0.5 * (-1.0)) = - (-0.5) + (-0.5)) = - (-1.0) = 1
```

同样，我们计算右侧数据集的熵：

```
p_0 = 3/6 = 0.5 且 p_1 = 3/6 = 0.5
```

`Entropyright = - ((0.5 * log_2(0.5)) + (0.5 * log_2(0.5))) = - ((0.5 * (-1.0)) + (0.5 * (-1.0)) = - (-0.5) + (-0.5)) = - (-1.0) = 1`

在计算了左侧和右侧的熵后，我们计算该决策节点的加权平均熵。注意划分左侧有 4 个数据点，右侧有 6 个数据点。如下：

```
Entropy_0 = 4/10 * 1.0 + 6/10 * 1.0 = 0.4 + 0.6 = 1.0
```

现在我们有了 `Entropy_Root` 和 `Entropy_x=1.0` 的值，可以如下计算划分点 `x=1.0` 的信息增益`GAIN`：

```
IG_x = Entropy_Root - Entropy_0 = 1.0 - 1.0 = 0
```
