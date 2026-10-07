
cross_val_score(); 正如我们之前做的那样，我们创建了一个准确率向量变量 `accuracies`，并将全局分类器变量 `ann_classifier_for_eval` 设置为估计器。

```python
accuracies = cross_val_score(estimator=ann_classifier_for_eval, x=X_train, y=y_train, cv=10, n_jobs=None)
```

所有操作与我们之前相同。

n_jobs（在深度学习中非常重要）：注意，这里 n_jobs = -1 对于 ANN 和所有深度学习技术至关重要。因为所有深度学习技术都是并行计算过程，这会让它们的运行速度变慢。此外，我们使用了 K 折交叉验证，这会让模型变慢 K 倍，模型实际上运行了 K 次，执行时间也增加了 K 倍。

因此，为了利用 CPU 的全部容量进行更快的计算，由于这个原因，我们对所有深度学习技术使用 n_jobs = -1（在这里如果我们需要在电脑上执行其他任务，则使用 n_jobs=0）。

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

accuracies - NumPy 对象数组

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

## 数据划分

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

## 使用构建的模型预测新数据

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

# 评估 ANN：k 折交叉验证
from sklearn.wrappers import KerasClassifier
from sklearn.model_selection import cross_val_score

# 创建创建 ANN 的函数
from keras.models import Sequential
from keras.layers import Dense

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

