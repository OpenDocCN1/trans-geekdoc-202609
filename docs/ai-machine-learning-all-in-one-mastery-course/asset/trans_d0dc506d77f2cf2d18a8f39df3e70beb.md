
# 监督学习

监督学习是一种机器学习类型，其中模型在标记的数据集上进行训练。数据集中每个训练示例都包括输入特征和相应的输出标签。监督学习的目标是学习从输入到输出的映射，以便模型能够对新数据做出准确预测。

## 关键特征

- **带标签的数据**：训练数据同时包含特征（输入）和标签（输出）。
- **训练过程**：模型从这些数据中学习以进行预测或分类。
- **目标**：最小化预测值与实际值之间的差异。

## 监督学习的类型

监督学习可以大致分为两种主要类型：

- **分类**：预测离散标签或类别。例如，判断一封邮件是否为“垃圾邮件”或“非垃圾邮件”。
- **回归**：预测连续值。例如，根据房屋特征预测房屋价格。

### 示例应用

| 类型 | 示例 | 用例 |
| --- | --- | --- |
| 分类 | 邮件垃圾邮件检测 | 过滤不需要的邮件 |
| 回归 | 房屋价格预测 | 估算房地产价值 |

## 2. 分类算法

### 2.1 逻辑回归

尽管名称如此，逻辑回归用于二分类问题。

#### 工作原理

逻辑回归对给定输入属于特定类别的概率进行建模。它使用逻辑函数将预测压缩在 0 到 1 之间。

#### 实现

```python
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Example dataset
data = pd.DataFrame({'Feature1': [1, 2, 3, 4, 5], 'Feature2': [2, 3, 4, 5, 6], 'Label': [0, 0, 1, 1, 1]})

# Splitting data
X = data[['Feature1', 'Feature2']]
y = data['Label']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Training the model
model = LogisticRegression()
model.fit(X_train, y_train)

# Making predictions
predictions = model.predict(X_test)

print("Accuracy:", accuracy_score(y_test, predictions))
```

### 2.2 决策树

决策树使用类似树的决策模型及其可能的结果。

#### 工作原理

决策树根据特征值将数据拆分为子集，递归创建表示不同决策的分支和叶子。

#### 实现

```python
from sklearn.tree import DecisionTreeClassifier

# Example dataset
data = pd.DataFrame({'Feature1': [1, 2, 3, 4, 5], 'Feature2': [2, 3, 4, 5, 6], 'Label': [0, 0, 1, 1, 1]})

# Splitting data
X = data[['Feature1', 'Feature2']]
y = data['Label']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Training the model
model = DecisionTreeClassifier()
model.fit(X_train, y_train)

# Making predictions
predictions = model.predict(X_test)

print("Accuracy:", accuracy_score(y_test, predictions))
```

### 2.3 随机森林

随机森林是一种集成方法，结合多个决策树以提高性能。

#### 工作原理

它构建多个决策树并聚合它们的预测结果以做出最终决策。

#### 实现

```python
from sklearn.ensemble import RandomForestClassifier

# Example dataset
data = pd.DataFrame({'Feature1': [1, 2, 3, 4, 5], 'Feature2': [2, 3, 4, 5, 6], 'Label': [0, 0, 1, 1, 1]})

# Splitting data
X = data[['Feature1', 'Feature2']]
y = data['Label']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Training the model
model = RandomForestClassifier()
model.fit(X_train, y_train)

# Making predictions
predictions = model.predict(X_test)

print("Accuracy:", accuracy_score(y_test, predictions))
```

## 3. 回归算法

### 3.1 线性回归

线性回归对输入特征与连续输出之间的关系进行建模。

#### 工作原理

它拟合一条线性方程来预测目标变量。

#### 实现

```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Example dataset
data = pd.DataFrame({'Feature1': [1, 2, 3, 4, 5], 'Feature2': [2, 3, 4, 5, 6], 'Target': [3, 4, 5, 6, 7]})

# Splitting data
X = data[['Feature1', 'Feature2']]
y = data['Target']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Training the model
model = LinearRegression()
model.fit(X_train, y_train)

# Making predictions
predictions = model.predict(X_test)

print("Mean Squared Error:", mean_squared_error(y_test, predictions))
```

### 3.2 岭回归

岭回归在损失函数中添加惩罚项以防止过拟合。

#### 工作原理

它通过添加 L2 正则化项来修改标准线性回归模型。

#### 实现

```python
from sklearn.linear_model import Ridge

# Example dataset
data = pd.DataFrame({'Feature1': [1, 2, 3, 4, 5], 'Feature2': [2, 3, 4, 5, 6], 'Target': [3, 4, 5, 6, 7]})

# Splitting data
X = data[['Feature1', 'Feature2']]
y = data['Target']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Training the model
model = Ridge(alpha=1.0)
model.fit(X_train, y_train)

# Making predictions
predictions = model.predict(X_test)

print("Mean Squared Error:", mean_squared_error(y_test, predictions))
```

### 3.3 支持向量机 (SVM)

SVM 可用于分类和回归任务。

#### 工作原理

SVM 找到在特征空间中最好地区分类别的超平面以进行分类，或为回归拟合最佳直线。

#### 实现

```python
from sklearn.svm import SVR

# Example dataset
data = pd.DataFrame({'Feature1': [1, 2, 3, 4, 5], 'Feature2': [2, 3, 4, 5, 6], 'Target': [3, 4, 5, 6, 7]})

# Splitting data
X = data[['Feature1', 'Feature2']]
y = data['Target']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Training the model
model = SVR(kernel='linear')
model.fit(X_train, y_train)

# Making predictions
predictions = model.predict(X_test)

print("Mean Squared Error:", mean_squared_error(y_test, predictions))
```

## 4. 模型评估指标

### 4.1 分类指标

#### 4.1.1 准确率

衡量正确分类实例的比例。

```python
from sklearn.metrics import accuracy_score

accuracy = accuracy_score(y_test, predictions)
print("Accuracy:", accuracy)
```

#### 4.1.2 精确率、召回率、F1 分数

用于评估分类模型在准确率之外的性能。

```python
from sklearn.metrics import classification_report

print(classification_report(y_test, predictions))
```

### 4.2 回归指标

#### 4.2.1 均方误差 (MSE)

衡量预测值与实际值之间的平均平方差。

```python
from sklearn.metrics import mean_squared_error

mse = mean_squared_error(y_test, predictions)
print("Mean Squared Error:", mse)
```

#### 4.2.2 R 平方分数

表示目标变量中可由特征预测的方差比例。

```python
from sklearn.metrics import r2_score

r2 = r2_score(y_test, predictions)
print("R-squared Score:", r2)
```

## 5. 监督学习最佳实践

### 5.1 数据准备

确保您的数据干净、准备充分且能代表您试图解决的问题。
