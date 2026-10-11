
# 使用 Python Scikit-Learn 库进行特征选择

机器学习算法从数据集中学习。数据集由特征组成。特征是指数据的单个特征或维度。特征也称为属性。例如，汽车数据集具有汽车型号、汽车颜色、座位容量等特征。选择合适的特征集不仅可以提高机器学习模型的性能，还可以加快算法的训练时间。在本章中，您将学习一些最常见的特征选择方法。您将使用 Python 的 Scikit-learn 库来演示各种特征选择方法。

## 4.1 基于方差的特征选择

具有常数值或非常相似值的特征在分类和回归等机器学习任务中并不起重要作用。因此，应从数据集中移除非常相似的特征。从数据集中移除非常相似的特征有多种方法。其中一种方法是计算特定特征的方差，并移除方差小于特定阈值的特征。方差低的特征其数据点之间具有较高的相似度，反之亦然。

让我们看一个基于方差的特征选择示例。以下脚本从数据仓库读取 `winequalit-red.csv` 数据集并打印数据集的表头。

**脚本 1：**
```
[Code for Script 1 - Image00180.jpg]
```

**输出：**
```
[Output for Script 1 - Image00181.jpg]
```

输出显示数据集有 12 列。接下来，我们将数据划分为特征集和标签集。

**脚本 2：**
```
[Code for Script 2 - Image00182.jpg]
```

基于方差的特征选择不依赖于输出标签。方差显示了一组数据分散的程度。您可以使用 Pandas DataFrame 的 `var()` 函数来查找所有特征的方差，如下所示。

**脚本 3：**
```
[Code for Script 3 - Image00183.jpg]
```

**输出：**

| 特征 | 方差 |
| :--- | :--- |
| fixed acidity | 3.031416 |
| volatile acidity | 0.032062 |
| citric acid | 0.037947 |
| residual sugar | 1.987897 |
| chlorides | 0.002215 |
| free sulfur dioxide | 109.414884 |
| total sulfur dioxide | 1082.102373 |
| density | 0.000004 |
| pH | 0.023835 |
| sulphates | 0.028733 |
| alcohol | 1.135647 |

Scikit-learn 库包含 `VarianceThreshold` 类，您可以使用它根据方差筛选特征。阈值被传递给构造函数的 `threshold` 参数。特征集被传递给 `VarianceThreshold` 类对象的 `fit()` 方法，如下面的脚本所示。以下脚本将筛选出方差值为 0.1 的所有特征。

**脚本 4：**
```
[Code for Script 4 - Image00184.jpg]
```

**输出：**
```
VarianceThreshold(threshold=0.1)
```

要获取选定的特征，您需要调用 `VarianceThreshold` 类的 `get_support()` 方法。该方法返回的值被传递给特征集的列列表，从而返回方差大于阈值的列。请参考以下脚本。

**脚本 5：**
```
[Code for Script 5 - Image00185.jpg]
```

**输出：**
```
Index(['fixed acidity', 'residual sugar', 'free sulfur dioxide', 'total sulfur dioxide', 'alcohol'], dtype='object')
```

您也可以使用以下脚本获取未被选中的属性名称。

**脚本 6：**
```
[Code for Script 6 - Image00186.jpg]
```

**输出：**
```
['volatile acidity', 'citric acid', 'chlorides', 'density', 'pH', 'sulphates']
```

要获取仅包含选定特征的最终数据集，您可以简单地移除基于方差阈值未被选中的特征。执行以下脚本以获取仅包含选定特征的最终数据集。

**脚本 7：**
```
[Code for Script 7 - Image00187.jpg]
```

**输出：**
```
[Output for Script 7 - Image00188.jpg]
```

基于方差的特征选择的主要问题之一是，它在特征选择时不考虑特征之间的相互关系。因此，使用基于方差的特征选择可能会选择冗余特征。为了避免选择冗余特征，您可以使用基于相关性的特征选择方法。

## 4.2 基于相关性的特征选择

在基于相关性的特征选择中，通过以下步骤选择特征：

1.  计算所有特征之间的相互相关性。
2.  设置相关性阈值。
3.  将与任何其他特征的相互相关性大于相关性阈值的特征从数据集中移除。

