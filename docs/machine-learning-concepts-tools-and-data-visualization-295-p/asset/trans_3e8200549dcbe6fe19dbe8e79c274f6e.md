

# 使用 Microsoft Azure Machine Learning Studio 集成创建预测模型

要修改 Python 脚本，点击图 8-20 中 Python Script Properties 窗口右上角的框。
参考图 8-21 中“Execute Python”块的使用来理解其工作原理。

![](img/3c3c87d78136583581b0cf0620f5ae66_151_0.png)

图 8-20 Python 脚本修改

![](img/3c3c87d78136583581b0cf0620f5ae66_151_1.png)

图 8-21 Execute Python 块的使用方法

# 136 机器学习：概念、工具与数据可视化

在 Python Script 窗口底部输入代码，如图 8-22 所示。

当你完成 Python 脚本的编写后，点击底部菜单中的“Run”按钮完成学习。完成后，右键点击“Execute Python Script”块，然后点击 Python Device 项目上的“Visualize”以查看结果，如图 8-23 所示。

图 8-24 的结果显示数据已正确输出。

![](img/3c3c87d78136583581b0cf0620f5ae66_152_0.png)

图 8-22 Python 脚本编辑

# 源代码 (8-22)

```python
import pandas as pd
def azureml1_main(dataframe1 = None):
    print('Input pandas.DataFrame #1: \r\n\n{0}'.format(dataframe1))
    return dataframe1,
```

# 使用 Microsoft Azure Machine Learning Studio 集成创建预测模型 137

![](img/3c3c87d78136583581b0cf0620f5ae66_153_0.png)

图 28-23 使用 Python 进行的数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_153_1.png)

图 28-24 使用 Python 脚本的数据输出结果

## 8.2.1 使用 Python 脚本实现 K-Means

使用“Select Columns in Dataset”块（如图 28-25 所示），选择要发送到“Execute Python Script”块的列。

然后从调色中导入并放置“Execute Python Script”块，如图 28-26 所示。

# 机器学习：概念、工具与数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_154_0.png)

图-8-25 用于实现算法的选择列

![](img/3c3c87d78136583581b0cf0620f5ae66_154_1.png)

图-8-26 Python 集成布局

要修改 Python 脚本，点击图 8-27 中 Python Script Properties 窗口右上角的框。
要应用 K-Means 算法，将“Sepal.Length”和“Sepal. Width”的值设置为特征，如图 8-28 所示。上面的代码是为创建三个簇编写的。代码如下。

# 使用 Microsoft Azure Machine Learning Studio 集成创建预测模型 139

![](img/3c3c87d78136583581b0cf0620f5ae66_155_0.png)

图 8-27 Python 脚本修改

![](img/3c3c87d78136583581b0cf0620f5ae66_155_1.png)

图 8-28 Python 脚本编辑

# 源代码 (8-28)

```python
import pandas as pd
from sklearn.cluster import KMeans
def azureml_main(dataframe1 = None):
    feature = dataframe1[['Sepal.Length','Sepal.Width']]

    model = KMeans(n_clusters=3)
    model.fit(feature)
    predict = pd.DataFrame(model.predict(feature))
    predict.columns=['predict']

    r = pd.concat([feature,predict], axis=1)
print(r)
return dataframe1,
```

# 140 机器学习：概念、工具与数据可视化

使用图 8-29 中的可视化来验证应用于 Python 脚本的结果是否保持完整。

如图 8-30 所示，你可以看到取决于“Sepal.Length”和“Sepal.Width”值的“Predict”值。预测值是簇群组。

![](img/3c3c87d78136583581b0cf0620f5ae66_156_0.png)

图 8-29 K-Means 结果可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_156_1.png)

图 8-30 使用 Python 脚本的 K-Means 结果

# 使用 Azure Machine Learning 脚本创建预测模型 141

| Sepal length | Sepal width | predict |
|---|---|---|
| 0 | 5.1 | 3.5 | 2 |
| 1 | 4.9 | 3.0 | 2 |
| 2 | 4.7 | 3.2 | 2 |
| 3 | 4.6 | 3.1 | 2 |
| 4 | 5.0 | 3.6 | 2 |
| 5 | 5.4 | 3.9 | 2 |
| 6 | 4.6 | 3.4 | 2 |
| 7 | 5.0 | 3.4 | 2 |
| 8 | 4.4 | 2.9 | 2 |
| 9 | 4.9 | 3.1 | 2 |
| 10 | 5.4 | 3.7 | 2 |
| 11 | 4.8 | 3.4 | 2 |
| 12 | 4.8 | 3.0 | 2 |
| 13 | 4.3 | 3.5 | 2 |
| 14 | 5.8 | 4.0 | 2 |
| 15 | 5.7 | 4.4 | 2 |
| 16 | 5.4 | 3.9 | 2 |
| 17 | 5.1 | 3.5 | 2 |
| 18 | 5.7 | 3.8 | 2 |
| 19 | 5.1 | 3.8 | 2 |
| 20 | 5.4 | 3.4 | 2 |
| 21 | 4.6 | 3.6 | 2 |
| 22 | 5.0 | 3.0 | 2 |
| 23 | 5.1 | 3.3 | 2 |
| 24 | 4.8 | 3.4 | 2 |
| 25 | 5.2 | 3.0 | 2 |
| 26 | 5.0 | 3.4 | 2 |
| 27 | 5.2 | 3.5 | 2 |
| 28 | 5.2 | 3.2 | 2 |
| 29 | 4.7 | ... | 2 |
| 120 | 6.9 | 3.2 | 1 |
| 121 | 5.6 | 2.8 | 0 |
| 122 | 7.7 | 2.7 | 1 |
| 123 | 6.3 | 2.7 | 1 |
| 124 | 7.2 | 3.3 | 1 |
| 125 | 6.7 | 3.2 | 1 |
| 126 | 6.2 | 2.8 | 0 |

![](img/3c3c87d78136583581b0cf0620f5ae66_157_0.png)

图 8-31 使用 Python 的 K-Means

如图 8-31 所示，你可以看到应用于 Python 脚本的结果。

# 8.3 练习题

Q1. 燃料类型是什么？
Q2. 说明 Python 脚本如何提高准确性。

# 第 9 章 预测价格

数据集有 205 行，包含 26 个属性。

# 表 9-1 数据集

| Attribute | Distribution |
|---|---|
| Sepal length | |
| Sepal width | |
| predict | |
| 0 | 5.1 | 3.5 | 2 |
| 1 | 4.9 | 3.0 | 2 |
| 2 | 4.7 | 3.2 | 2 |
| 3 | 4.6 | 3.1 | 2 |
| 4 | 5.0 | 3.6 | 2 |
| 5 | 5.4 | 3.9 | 2 |
| 6 | 4.6 | 3.4 | 2 |
| 7 | 5.0 | 3.4 | 2 |
| 8 | 4.4 | 2.9 | 2 |
| 9 | 4.9 | 3.1 | 2 |
| 10 | 5.4 | 3.7 | 2 |
| 11 | 4.8 | 3.4 | 2 |
| 12 | 4.8 | 3.0 | 2 |
| 13 | 4.3 | 3.5 | 2 |
| 14 | 5.8 | 4.0 | 2 |
| 15 | 5.7 | 4.4 | 2 |
| 16 | 5.4 | 3.9 | 2 |
| 17 | 5.1 | 3.5 | 2 |
| 18 | 5.7 | 3.8 | 2 |
| 19 | 5.1 | 3.8 | 2 |
| 20 | 5.4 | 3.4 | 2 |
| 21 | 4.6 | 3.6 | 2 |
| 22 | 5.0 | 3.0 | 2 |
| 23 | 5.1 | 3.3 | 2 |
| 24 | 4.8 | 3.4 | 2 |
| 25 | 5.2 | 3.0 | 2 |
| 26 | 5.0 | 3.4 | 2 |
| 27 | 5.2 | 3.5 | 2 |
| 28 | 5.2 | 3.2 | 2 |
| 29 | 4.7 | ... | 2 |
| 120 | 6.9 | 3.2 | 1 |
| 121 | 5.6 | 2.8 | 0 |
| 122 | 7.7 | 2.7 | 1 |
| 123 | 6.3 | 2.7 | 1 |
| 124 | 7.2 | 3.3 | 1 |
| 125 | 6.7 | 3.2 | 1 |
| 126 | 6.2 | 2.8 | 0 |

