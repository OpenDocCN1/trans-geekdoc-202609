
# 第 4 部分 评估、改进与调优 ANN

## K 折交叉验证

```python
# 第 4 部分 评估、改进与调优 ANN
# K 折交叉验证
from keras.wra import KerasClassifier
from sklearn.model_selection import cross_val_score # 结合 Keras & Scikit-Learn
```

```python
# 创建一个创建 ANN 的函数
from keras.models import Sequential
from keras.layers import Dense
def build_ann_classifier():
    # 初始化 ANN
    ann = Sequential()
    ann.add(Dense(units=6, kernel_initializer='uniform', activation='relu', input_dim=11)) # "输入层 & 第一个隐藏层"
    ann.add(Dense(units=6, kernel_initializer='uniform', activation='relu')) # 第二个隐藏层"
    ann.add(Dense(units=1, activation='sigmoid')) # "输出层"
    ann.compile(optimizer='adam', loss='binary_crossentropy', metrics=['Accuracy']) # 编译 ANN
    return ann
```

```python
ann_classifier_for_eval = KerasClassifier(build_fn=build_ann, batch_size=10, epochs=100) # 创建一个 ANN 分类器
accuracies = cross_val_score(estimator=ann_classifier_for_eval, x=X_train, y=y_train, cv=10, n_jobs=None) # 使用 10 折交叉编译 10 次 ANN
```

```python
mean_acc = accuracies.mean()
st_dvi_acc = accuracies.std()
```

为了比较平均值和标准差，我们使用：

```python
mean_acc = accuracies.mean()
st_dvi_acc = accuracies.std()
```

平均准确率为 83.3，标准差为 1%。我们处于以下类别：

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_361_0.png)

`accuracies` - NumPy 对象数组

| | |

| :--- | :--- |

| 0 | 0.8325 |

| 1 | 0.83875 |

| 2 | 0.83375 |

| 3 | 0.8275 |

| 4 | 0.85 |

| 5 | 0.83375 |

| 6 | 0.835 |

| 7 | 0.83375 |

| 8 | 0.81 |

| 9 | 0.84625 |

| | type | count | value |

| :--- | :--- | :--- | :--- |

| mean_acc | float64 | 1 | 0.833850004768372 |

| st_dvi_acc | float64 | 1 | 0.010253814766620795 |

## 所有代码汇总（已处理）

```python
# 人工神经网络
# 安装：TensorFlow, Keras 和 Theano 库。
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
```

## 第 1 部分：数据预处理

```python
# 提取数据
dataset = pd.read_csv('Churn_Modelling.csv')
# X = dataset.iloc[:,3:-1].values # 这也可以用
X = dataset.iloc[:,3:13].values # 从索引 3 开始的所有列，排除索引 13（索引列）
y = dataset.iloc[:, 13].values # 最后一列
```

```python
# 编码分类数据
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
from sklearn.compose import ColumnTransformer

Encode("Gender", label=LabelEncoder(), "Gender" = "3rd-column", X[:,2])
label_encode = LabelEncoder()
label_encode.fit(X[:,2])
# X = np.array(X) 转换为 numpy 数组，如果我们使用了 "X = dataset.iloc[:, 3:13].values"
X = np.array(X)  # 如果 X 不是数组，则需要这样做，“values" 值不生效
X[:,2] = label_encode.fit_transform(X[:,2])
print(X)
```

```python
# 对于一个数据集，我们仍然可以使用列 "Key" 来进行编码
X["Gender"] = label_encode.fit_transform(X["Gender"])

Encode("Geography", OneHotEncoder(), "Geography" = "2nd-column", [1])
ct = ColumnTransformer(transformers=[("", OneHotEncoder(), [1]], remainder="passthrough")
X = ct.fit_transform(X)
X = np.array(X) # 转换为 numpy 数组
print(X)
X[:,1] = [] # 排除第0 列
```

### 数据划分

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
```

## 特征缩放

```python
from sklearn.preprocessing import StandardScaler

# Y 变量不需要缩放：分类

st = StandardScaler()

X_train = st.fit_transform(X_train)

X_test = st.transform(X_test)
```

## 第 2 部分：创建 ANN

```python
# 导入 "keras" 库

import keras

from keras.models import Sequential

# 2. 初始化 ANN

classifier = Sequential()

# 3. 添加 "输入层"

classifier.add(Dense(units=6, kernel_initializer="uniform", activation="relu", input_dim=11))

# 4. 添加第二个 "隐藏层"

classifier.add(Dense(units=6, kernel_initializer="uniform", activation="relu"))

# 5. 添加 "输出层"

classifier.add(Dense(units=1, kernel_initializer="uniform", activation="sigmoid"))

# 6. 编译 ANN

classifier.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])

# 7. 训练模型；拟合训练集 ANN（batch size 和 epoch）

classifier.fit(X_train, y_train, batch_size=10, epochs=100)
```

## 第 3 部分：预测与评估模型

```python
# 预测

y_pred = classifier.predict(X_test)

# 将概率转换为 'true/false' 形式，因为 1 表示离开银行

y_pred = (y_pred > 0.5)

# 使用 "混淆矩阵"

# 输出格式。函数是小写

from sklearn.metrics import confusion_matrix

cm = confusion_matrix(y_test, y_pred)

# cm 的参数：y_true: 真实值，y_pred: 预测值

accuracy = (cm[0][0] + cm[1][1])/y_test.shape[0]

print(f"Accuracy: {accuracy}")
```

### 使用构建的模型预测新数据

使用我们的 ANN 模型预测以下信息的客户将离开银行：
- 国家：法国
- 信用评分：600
- 性别：男
- 年龄：40 岁
- 工龄：3 年
- 余额：60000
- 该客户有信用卡吗？是
- 是否是活跃会员：是
- 估计薪水：54000

我们要和该客户告拜吗？

```python
# 首先在我们的 x_train 格式中创建一个 np.array

# 重塑我们的 x_train 会更简单

# 使用 [[]] 定义二维数组的一行

new_dt_pt = np.array([[0.0, 0.0, 600, 1, 40, 3, 60000.0, 2, 1, 54000.0]])

new_dt_pt = st.transform(new_dt_pt) # 缩放

predict_data_pt = (classifier.predict(new_dt_pt) > 0.5) # 预测数据点
```

## 第 4 部分：评估、改进与调优 ANN

### 评估 ANN：k 折交叉验证

```python
from sklearn.wrappers import KerasClassifier
from sklearn.model_selection import cross_val_score
```

```python
# 创建创建 ANN 的函数
from keras.models import Sequential
from keras.layers import Dense
```

```python
# 初始化 ANN 模型

def ann_classifier():

    ann = Sequential()

    ann.add(Dense(units=6, kernel_initializer='uniform', activation='relu', input_dim=11)) # "第一个隐藏层"

    ann.add(Dense(units=6, kernel_initializer='uniform', activation='relu')) # "第二个隐藏层"

    ann.add(Dense(units=1, kernel_initializer='uniform', activation='sigmoid')) # "输出层"

    ann.compile(optimizer='adam', loss='binary_crossentropy', metrics=['Accuracy']) # 编译 ANN

    return ann
```

```python
accuracies = cross_val_score(estimator=ann_classifier(), x=X_train, y=y_train, cv=10, n_jobs=5) # 使用 10 折编译 ANN 分类器

mean_acc = accuracies.mean()

std_acc = accuracies.std()
```

## 改进 ANN：Dropout 正则化

## 调优 ANN：网格搜索

```python
# python keras_ANN_eval_KFCV.py
```

## 11.3.3 Dropout 正则化：改进 ANN

从上面看到我们的模型正在使用 K-Fold-CV，我们可以通过修改我们的来改进它...

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_364_0.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_364_1.png)

应用 dropout：我们使用 `add()` 在层中添加 `Dropout`。我们在每一层之后执行此操作。

```python
# 添加“输入层”和“第一个隐藏层”
ann_classifier.add(Dense(units=6, kernel_initializer="uniform", activation="relu", input_dim=11))
ann_classifier.add(Dropout(p=0.1))
```

```python
# 添加“第二个隐藏层”
ann_classifier.add(Dense(units=6,
```

`p = 0.1`：`p` 是范围在 `(0, 1)` 内的浮点数。它是你想要丢弃的输入比例。也就是你想要在每次迭代中丢弃或禁用的神经元比例。在较新版本中，`p` 被 `rate` 取代。

例如：如果我们有 10 个神经元，如果我们选择 `p=0.1`，那么在每次迭代中，有 10% 的概率有一个神经元被禁用。如果我们等于 `p=0.2`，则会有两个神经元被禁用。

我们应该输入什么值的 P(rate)？'p' 被替换为 "rate"

- 我们的建议是，当你发生过拟合时，尝试从 `p` 或 `rate` 值为 0.1、10 开始，如果这不能解决问题，你仍然过拟合，直到你找到更高的 `rate` 值并对其递量，例如增加 0.1。
- 所以先尝试 0.1，如果你仍然过拟合，就尝试 0.2。如果使用 0.3 仍然过拟合，请使用正则化来减少过拟合。
- `rate(p)` 值过高是不好的，当你禁用了某层的大部分神经元时，你不会得到过拟合，而是欠拟合；如果 `p=0.9`，则什么都不会被关闭。
- 通常，我们建议尝试 0.1，这样你就会接近过拟合，这应该就足够了。

在对第一个隐藏层应用 dropout 之后，我们需要复制代码行并将其应用于第二个隐藏层。

### 一次应用 dropout 的所有 ANN 结构

```python
# 1. 导入 keras 库和框架
import keras # 使用 Tensorflow 后端
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import Dropout
```

```python
# 2. 初始化 ann
ann_classifier = Sequential()
```

```python
# 3. 添加“输入层”和“第一个隐藏层”
ann_classifier.add(Dense(units=6, kernel_initializer="uniform", activation="relu", input_dim=11))
ann_classifier.add(Dropout(rate=0.1)) # 使用 'rate' 代替 'p'
```

```python
# 4. 添加“第二个隐藏层”
ann_classifier.add(Dense(units=6,
```

```python
# 5. 添加“输出层”
ann_classifier.add(Dense(units=1
```

```python
# 6. 编译
ann_classifier.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"]
```

```python
# 7. 训练模型
nann_classifier.fit(X_train, y_train, batch_size=10, epochs=100)
```

## 11.3 ANN 超参数调优

- **模型参数 (Model-parameter)**：是模型自己学习的参数。
- **超参数 (Hyper parameters)**：是我们我们在构建模型时固定的参数。这些是**迭代次数 (epoch)** 数、**批量大小 (batch size)**、**优化器 (optimizer)** 或**层 (layers)** 中的**神经元 (neurons)** 数量。

**参数调优与网格搜索 (Parameter-Tuning & Grid-Search)**：这是**改进**我们模型**性能**的真实手段，因为我们将对模型进行调优，并将找到最佳**超参数**，即最佳的**epoch**、**batch size**、**optimizer**，从而获得最大准确率的最佳 ANN。

- 我们的建议是在出现过拟合时，尝试从 `p` 或 `rate` 值为 0.1、10 开始，如果这不能解决问题，你仍然过拟合，直到你找到更高的 `rate` 值并对其递量，例如增加 0.1。
- 所以先尝试 0.1，如果你仍然过拟合，就尝试 0.2。如果使用 0.3 仍然过拟合，请使用正则化来减少过拟合。
- `rate(p)` 值过高是不好的，当你禁用了某层的大部分神经元时，你不会得到过拟合，而是欠拟合；如果 `p=0.9`，则什么都不会被关闭。
- 通常，我们建议尝试 0.1，这样你就会接近过拟合，这应该就足够了。

在对第一个隐藏层应用 dropout 之后，我们需要复制代码行并将其应用于第二个隐藏层。

### 一次应用 dropout 的所有 ANN 结构

```python
# 1. 导入 keras 库和框架
import keras # 使用 Tensorflow 后端
```
