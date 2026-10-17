
```
Epoch 7/100
=====================================
is 904us/step - loss: 0.3412 - accuracy: 0.8576
Epoch 8/100
=====================================
is 791us/step - loss: 0.3409 - accuracy: 0.8589
Epoch 9/100
=====================================
is 845us/step - loss: 0.3405 - accuracy: 0.8601
Epoch 10/100
=====================================
is 836us/step - loss: 0.3406 - accuracy: 0.8614
```

### 4.8.5 训练好的 ANN 模型的预测与评估

我们刚刚在训练集上训练了 `ANN`，现在是时候对测试集进行预测了。我们可以执行以下操作作为我们的分类模型。

```
y_pred = ann_classifier.predict(x_test)
```

在我们获得预测概率后，这些概率是测试集中 2000 名客户离开银行的概率。

现在我们可以通过混淆矩阵（`Confusion-matrix`）获取模型的准确率。我们在训练集上获得了 86% 的准确率，现在将使用测试集。

（注：原文后续描述存在大量逻辑重复和碎片，已根据文档工程师标准提取核心流程：）

- 我们设置阈值（例如 `0.5`）来决定预测结果是 `1`（离开）还是 `0`（留存）。
- 通过混淆矩阵来衡量这些客户的预测情况。
- 如果我们在测试集上获得了良好的准确率，银行就可以使用该模型对客户进行排序，找出哪些客户最可能离开银行，并使用数据挖掘技术深入分析为什么这一类别的客户最可能离开。

| 索引 | 概率 | 结果 |
|---|---|---|
| 0 | 0.204 | False |
| 1 | 0.308 | False |
| 2 | 0.100 | False |
| 3 | 0.033 | False |
| 4 | 0.052 | True |
| 5 | 0.918 | False |
| 6 | 0.020 | False |
| 7 | 0.084 | False |
| 8 | 0.122 | True |
| 9 | 0.937 | False |
| 10 | | |
| 11 | | |

然而，`predict` 方法返回 `[0, 1]` 范围内的概率。在混淆矩阵中我们只需要将这些概率转换为 'false' 或 'true'。我们设置阈值为 `0.5`。

```
y_pred = (y_pred > 0.5)
```

`y_pred > 0.5` 意味着客户将离开银行。现在我们可以进行混淆矩阵。如果我们需要预测敏感信息，例如预测客户是离开还是留在银行，那么 50% 的阈值是可以的。

| | | |
|---|---|---|
| 1 | 1550 | 45 |
| 2 | 230 | 75 |
| 1 | 1523 | 72 |
| 2 | 215 | 190 |

在 2000 次新观测中，我们获得了 1550 次正确预测和 230 次错误预测。

`Accuracy = (1550 + 175) / 2000 = 86%`

在新的观测上，我们得到的准确率是 86%。我们没有进行任何参数调优。所以我们还可以获得更好的准确率。

# 人工神经网络 (ANN)

## 安装 - Tensorflow, Keras 库

```python
# 库
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
```

## 第一部分：数据预处理

### 数据提取

```python
dataset = pd.read_csv('Churn_Modelling.csv')
X = dataset.iloc[:, 3:-1] # 使用部分
X = dataset.iloc[:, 3:13] # 从索引 3 开始，排除 13
y = dataset.iloc[:, 13] # 最后列
```

```python
# 编码类别数据
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
from sklearn.compose import ColumnTransformer
# 使用 LabelEncoder 编码 "Gender"。在第 3 列
# 如果使用，适用于 numpy 数组
label_encode = LabelEncoder()
X[:, 2] = label_encode.fit_transform(X[:, 2])
print(X)
```

```python
# 对于数据集，我们仍然可以使用列列进行编码
# 使用 OneHotEncoder 编码 "Geography"。在第 2 列，因此索引为 1
X["Gender"] = label_encode.fit_transform(X["Gender"]) # 注意：此处原文逻辑与变量名有冲突
ct = ColumnTransformer(transformers=["encoding", OneHotEncoder(), [1]], remainder='passthrough')
# remainder='passthrough' 让剩余列保持不变
X = ct.fit_transform(X)
X = np.array(X) # 将输出转换为 NumPy 数组
print(X)
X = X[:, 1:] # 排除索引 0 列以避免虚拟变量类型
```

```python
# 数据划分
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
```

```python
# 数据划分后的特征缩放
# 特征缩放
from sklearn.preprocessing import StandardScaler
# y 因变量不需要缩放：类别变量，0 和 1
st = StandardScaler()
X_train = st.fit_transform(X_train)
X_test = st.fit_transform(X_test)
```

```python
# 第二部分：创建 ANN 模型
# 1. 导入 "keras" 库和包
```

```python
# tensorflow import keras
import keras # 使用 TensorFlow 后端
from keras.models import Sequential
from keras.layers import Dense
```

```python
# 2. 初始化 ANN
ann_classifier = Sequential()
```

```python
# 3. 添加“输入层”和“第一个隐藏层”
ann_classifier.add(Dense(6, kernel_initializer='uniform', activation='relu', input_dim=11))
```

```python
X[:, 2] = le.fit_transform(X[:, 2])
print(X)
```

### 编码“Geography”列

```python
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder
ct = ColumnTransformer(['encoder', OneHotEncoder(), [2]], remainder='passthrough')
X = np.array(ct.fit_transform(X))
print(X)
```

### 特征节点

```python
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
X = sc.fit_transform(X)
print(X)
```

### 将数据集划分为训练集和测试集

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
```

## 第 2 部分 - 构建 ANN

```python
# 添加输入层和第一个隐藏层
ann.add(tf.keras.layers.Dense(units=6, activation='relu'))

# 添加第二个隐藏层
ann.add(tf.keras.layers.Dense(units=6, activation='relu'))

# 添加输出层
ann.add(tf.keras.layers.Dense(units=1, activation='sigmoid'))
```

## 第 3 部分 - 训练 ANN

```python
# 编译优化器
ann.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])

# 在训练集上训练 ANN
ann.fit(X_train, y_train, batch_size=32, epochs=10)
```

## 第 4 部分 - 预测并评估模型

```python
# 预测测试结果
y_pred = ann.predict(X_test)
y_pred = (y_pred > 0.5)
print(np.concatenate((y_pred.reshape(len(y_test),1), y_test.reshape(len(y_test),1))))
```

```python
# 制作混淆矩阵
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_test, y_pred)
print(cm)
```

> `GPU` 上的深度学习：`GPU` 是用于图形任务的处理器。在计算效率方面，`GPU` 比 `CPU` 更强大，因为它拥有许多核心，并且每秒能够运行更多的浮点运算。
> `GPU` 专门用于高强度密集型任务和并行计算，这正是神经网络的特点。
> 当我们在神经网络中传播神经元的激活值时，这恰好涉及并行计算，当误差反向传播到神经网络时也是如此。因此，由于大量的并行计算，`GPU` 是更好的选择。
> `Tensorflow`：在初始阶段的警告、错误方面具有胜优势。对于致命错误有一个 `Error`。
> 在 `conda` 环境中，我们需要安装所有包：`TensorFlow`, `Keras`, `pandas`, `Scikit-learn`, `matplotlib` 等。
> 更新后的导师版本使用了 `TF.keras`，而我们只使用了 `keras`。

# 新文档

添加第一层 `ANN` 层 `add(Dense(units=6, activation='relu', kernel_initializer='uniform', input_dim = 11))`

```python
classifier.add(Dense(units = 6, kernel_initializer ='uniform', activation = 'relu'))
```

添加第二个隐藏层

```python
classifier.add(Dense(units = 6, kernel_initializer ='uniform', activation = 'relu'))
```

要在 `TF 2.0` 中运行 `TF 1.x` 行为可以执行

```python
import tensorflow.compat.v1 as tf
tf.disable_v2_behavior()
```

但这样无法受益 `TF 2.0` 的许多改进。更多细节请参阅迁移指南

https://www.tensorflow.org/guide/migrate

## 首次测试 tensorflow

```python
>>> import tensorflow as tf 
>>> hello = tf.constant("hello TensorFlow!")
>>> sess=tf.Session()
>>> sess.run(hello)
```

验证你的安装只需输入：
