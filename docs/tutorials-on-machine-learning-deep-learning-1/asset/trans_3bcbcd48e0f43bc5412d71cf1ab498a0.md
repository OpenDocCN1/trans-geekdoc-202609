
[2] 虚拟变量陷阱（Dummy Variable Trap）：然而，Python 的线性回归库已经处理了虚拟变量陷阱。我们不需要像以前那样手动处理。

- 这意味着对于某些需要的软件/库，你需要手动处理虚拟变量陷阱。

```python
# 避免虚拟变量陷阱：省略一个虚拟变量
# 从第2列开始选择所有列
x_go = x_encoded[:, 1:]
y_go = np.array(y) # 将 DataFrame 转换为向量/数组
```

[3] 测试大小：40 个训练集，10 个测试。
# 将数据集划分为训练集和测试集
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X_go, y_go, test_size=0.2, random_state=0)

[4] 创建模型：在训练集上拟合多元线性回归
# 在训练集上拟合多元线性回归
from sklearn.linear_model import LinearRegression
regResor = LinearRegression()
regResor.fit(X_train, y_train)

[5] 预测：由于该模型是多维的，无法为此模型画图。
# 在测试集 X_test 上进行预测
y_pred = regResor.predict(X_test)

注意：我们可以将 dataframe 转换为 Array 对象。

| Index | Profit | Index | Profit | Index | Profit |
|---|---|---|---|---|---|
| 0 | 103815 | 28 | 103282 | 0 | 103015 |
| 1 | 132582 | 11 | 144259 | 1 | 132582 |
| 2 | 132448 | 10 | 146122 | 2 | 132448 |
| 3 | 71976.1 | 41 | 77978.8 | 3 | 71976.1 |
| 4 | 178537 | 29 | 191050 | 4 | 191050 |
| 5 | 116611 | 27 | 105098 | 5 | 116611 |
| 6 | 67851.7 | 38 | 81229.1 | 6 | 67851.7 |
| 7 | 96791.7 | 31 | 97483.6 | 7 | 97483.6 |
| 8 | 113969 | 22 | 110952 | 8 | 113952 |
| 9 | 167921 | 14 | 166188 | 9 | 166188 |

# 练习版本

```python
# 基础库
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

# 数据集
daset = pd.read_csv('50_Startups.csv')
X = dataSet.iloc[:, :-1] # 除去最后一列
y = dataSet.iloc[:, 4] # 第4行
```

# 类别转数值
from sklearn.transformer import ColumnTransformer
from sklearn.prepreprocessing import OneHotEncoder
columtransformer = ColumnTransformer(transformers=["encoder", OneHotEncoder(), [3]], remainder="passthrough")
X_encoded = np.array(columtransformer.fit_transform(X))
# 最后列被虚拟列替换（最后3列）

# 将数据集划分为训练集和测试集
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X_go, y_go, test_size=0.2, random_state=0)

# 在训练集上拟合多元线性回归
from sklearn.linear_model import LinearRegression
regressor = LinearRegression()
regressor.fit(X_train, y_train)

# 在测试集 X_test 上预测
Y_pred = regressor.predict(X_test)

# python prctc_mul_lin_regn.py

# 答案

# 多元线性回归

# 导入库
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

# 导入数据集
dataset = pd.read_csv('00_Startups.csv')
X = dataset.iloc[:, :-1].values # 排除最后一列
y = dataset.iloc[:, -1].values # 选择最后一列
print(X)

# 编码类别数据
from sklearn.transformer import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder
columtransformer = ColumnTransformer(transformers=["encoder", OneHotEncoder(), [3]], remainder="passthrough")
X_encoded = np.array(columtransformer.fit_transform(X))
print(X)

# 将数据集划分为训练集和测试集
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X_encoded, y, test_size=0.2, random_state=0)

# 在训练集上训练多元线性回归
from sklearn.linear_model import LinearRegression
regressor = LinearRegression()
regressor.fit(X_train, y_train)

# 在测试集 X_test 上预测
Y_pred = regressor.predict(X_test)

#2.2 回向消除（Backward Elimination）
当我们构建模型时，使用了所有独立变量。但在这些独立变量中，某些是非常显著的。如果我们从模型中移除这些非统计显著的变量，仍然可以进行预测。

## 需要回向消除：最优线性回归模型
在上一节中，我们讨论并成功创建了线性回归模型，其中我们包含了变量（研发支出、行政支出、营销支出）和一个因变量（利润）。但这并不是最优的，因为我们包含了所有的独立变量，并且不知道哪个变量的影响最大，哪个影响最小，不必要的特征会增加模型的复杂度。因此，只保留显著特征并保持简单模型以获得更好的结果。因此，为了优化模型性能，我们将使用回向消除。这个过程通过包含影响最大的特征并移除影响最小的特征来优化模型性能。
