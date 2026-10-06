
这里是 7 岁男孩偏好分类的完整决策树。如果你想以更高质量查看整棵树，请执行该代码。

![](img/d75fea3635f5553f1cb0585b399b1b4b_149_0.png)

同样，我们可以使用决策树来解决基于分类的不同类型的问题。但你可能会问，树是如何创建这些比较或划分的呢？这并不是必须知道，但你应该了解。首先，算法使用下面的公式为每个属性计算基尼指数（gini index）：

$p^2 + q^2$

这是成功(p) 和失败(q) 概率平方之和。然后，数据集被分为两个行列表，具有一个属性的索引和该属性的划分值。接着，它通过评估划分的成本(gini)来找到最佳的划分方式。

## 逻辑回归

逻辑回归是一种模型，它可以将输出结果预测为“是”或“否”，分别对应数值 1 或 0。我们可以使用这类模型将一天分类为下雨或不下雨，将一个人分类为健康或患病等等。但是有不同类型的逻辑回归用于不同的情况。

## 二元逻辑回归

二元或二分类逻辑回归用于预测精确的两个结果，即 1（正）或 0（负）。

让我们使用一个数据集来预测是否会下雨，提供了温度和湿度百分比作为输入。你可以从这里下载数据集 -

让我们一起导入模块和数据集。这次我们将从 sklearn 中导入 `linear_model` 和 `train_test_split`。

```
import pandas
from sklearn import linear_model
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
```

![](img/d75fea3635f5553f1cb0585b399b1b4b_150_0.png)

```
In [1]: import pandas
from sklearn import linear_model
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
```

我们还从 `sklearn.metrics` 导入了 `accuracy_score()` 函数来计算我们模型的准确率。

现在我们可以导入数据集，这次让我们按原样查看它。

```
In [2]: import pandas
from sklearn import linear_model
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
dt = pandas.read_csv('Rainfall_data.csv')
```

| Unnamed: 0 | Temperature | Humidity% | Rain |
|---|---|---|---|---|
| 0 | 0 | 34 | 74.2 | Yes |
| 1 | 1 | 19 | 68.2 | No |
| 2 | 2 | 28 | 67.2 | Yes |
| 3 | 3 | 29 | 66.6 | Yes |
| 4 | 4 | 26 | 57.9 | Yes |
| ... | ... | ... | ... | ... |
| 19995 | 19995 | 30 | 77.9 | Yes |
| 19996 | 19996 | 20 | 74.8 | Yes |
| 19997 | 19997 | 14 | 69.4 | No |
| 19998 | 19998 | 20 | 60.6 | No |
| 19999 | 19999 | 22 | 64.8 | No |

20000 行 × 4 列

如你所示，我们有 20000 行 4 列数据！现在我们可以移动到新单元格，并将数据划分为训练-测试输入和训练-测试输出。

```
In [3]: Input = dt.drop(columns=['Unnamed: 0', 'Rain'])
Output = dt['Rain']
inp_X, tst_X, out_y, tst_y = train_test_split(
Input.values,Output,test_size=0.01)
```

我们将输入特征（即温度）存储在 `Input` 中，将输出（即天气，是或否）存储在 `Output` 中。然后我们将这些值传递给 `train_test_split()` 函数，并将数据划分为训练输入、测试输入、训练输出和测试输出，其中测试大小为 0.01（即 1%，即 200）。

我们可以创建一个逻辑回归模型 `CModel` 并训练它。

```
In [4]: Input = dt.drop(columns=['Unnamed: 0', 'Rain'])
Output = dt['Rain']
inp_X, test_X, out_y, test_y = train_test_split(
Input.values,Output,test_size=0.01)
CModel = linear_model.LogisticRegression()
CModel.fit(inp_X, out_y)
```

Out [4]: LogisticRegression()

```

所以我们的模型已经准备好进行预测了，让我们移动到新单元格让模型进行预测。我们将比较这些值并打印准确率。

```
In [5]: from sklearn import preprocessing
pred_y = CModel.predict(test_X)
Enc = preprocessing.LabelEncoder().fit(['Yes', 'No'])
cmp = pandas.DataFrame({'Predicted':pred_y,'Actual':test_y})
print('Accuracy Score:',accuracy_score(test_y,pred_y))
```

Out [5]: 0.91

![](img/d75fea3635f5553f1cb0585b399b1b4b_151_0.png)

所以我们的模型已经准备好进行预测了，让我们移动到新单元格让模型进行预测。我们将比较这些值并打印准确率。

Out [5]: 0.91

所以我们的模型已经准备好进行预测了，让我们移动到新单元格让模型进行预测。我们将比较这些值并打印准确率。

Out [5]: 0.91

所以我们的模型已经准备好进行预测了，让我们移动到新单元格让模型进行预测。我们将比较这些值并打印准确率。

Out [5]: 0.91

所以我们的模型已经准备好进行预测了，让我们移动到新单元格让模型预测

让我们使用一个数据集来预测是否会下雨，提供了温度和湿度百分比作为输入。你可以从这里下载数据集 -

让我们一起导入模块和数据集。这次我们将从 sklearn 中导入 `linear_model` 和 `train_test_split`。

```
import pandas
from sklearn import linear_model
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
```

![](img/d75fea3635f5553f1cb0585b399b1b4b_150_0.png)

```
In [1]: import pandas
from sklearn import linear_model
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
```

我们还从 `sklearn.metrics` 导入了 `accuracy_score()` 函数来计算我们模型的准确率。

现在我们可以导入数据集，这次让我们按原样查看它。

```
In [2]: import pandas
from sklearn import linear_model
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
dt = pandas.read_csv('Rainfall_data.csv')
```

| Unnamed: 0 | Temperature | Humidity% | Rain |
|---|---|---|---|---|
| 0 | 0 | 34 | 74.2 | Yes |
| 1 | 1 | 19 | 68.2 | No |
| 2 | 2 | 28 | 67.2 | Yes |
| 3 | 3 | 29 | 66.6 | Yes |
| 4 | 4 | 26 | 57.9 | Yes |
| ... | ... | ... | ... | ... |
| 19995 | 19995 | 30 | 77.9 | Yes |
| 19996 | 19996 | 20 | 74.8 | Yes |
| 19997 | 19997 | 14 | 69.4 | No |
| 19998 | 19998 | 20 | 60.6 | No |
| 19999 | 19999 | 22 | 64.8 | No |

20000 行 × 4 列

如你所示，我们有 20000 行 4 列数据！现在我们可以移动到新单元格，并将数据划分为训练-测试输入和训练-测试输出。

```
In [3]: Input = dt.drop(columns=['Unnamed: 0', 'Rain'])
Output = dt['Rain']
inp_X, tst_X, out_y, tst_y = train_test_split(
Input.values,Output,test_size=0.01)
```

我们将输入特征（即温度）存储在 `Input` 中，将输出（即天气，是或否）存储在 `Output` 中。然后我们将这些值传递给 `train_test_split()` 函数，并将数据划分为训练输入、测试输入、训练输出和测试输出，其中测试大小为 0.01（即 1%，即 200）。

我们可以创建一个逻辑回归模型 `CModel` 并训练它。

```
In [4]: Input = dt.drop(columns=['Unnamed: 0', 'Rain'])
Output = dt['Rain']
inp_X, test_X, out_y, test_y = train_test_split(
Input.values,Output,test_size=0.01)
CModel = linear_model.LogisticRegression()
CModel.fit(inp_X, out_y)
```

Out [4]: LogisticRegression()

```

所以我们的模型已经准备好进行预测了，让我们移动到新单元格让模型进行预测。我们将比较这些值并打印准确率。

```
In [5]: from sklearn import preprocessing
pred_y = CModel.predict(test_X)
Enc = preprocessing.LabelEncoder().fit(['Yes', 'No'])
cmp = pandas.DataFrame({'Predicted':pred_y,'Actual':test_y})
print('Accuracy Score:',accuracy_score(test_y,pred_y))
```

Out [5]: 0.91

![](img/d75fea3635f5553f1cb0585b399b1b4b_151_0.png)
