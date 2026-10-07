

```python
from sklearn.model_selection import train_test_split
# 0.25 的大小意味着总观测值的“1/4”
x_train, x_test, y_train, y_test = train_test_split(X, y, test_size=0.25, random_state=0)

# 特征缩放
from sklearn.preprocessing import StandardScaler
# y不需要缩放：分类变量
sc_x = StandardScaler()
X_scaled = sc_x.fit_transform(X)
st_x = StandardScaler()
x_train = st_x.fit_transform(X_train)
test = st_x.transform(X_test)
```

```python
-----
# 特征缩放
from sklearn.preprocessing import StandardScaler
# y不需要缩放：分类变量
sc_x = StandardScaler()
X_scaled = sc_x.fit_transform(X)
```

```python
# 数据划分
from sklearn.model_selection import train_test_split
# 0.25 的大小意味着总观测值的“1/4”
x_train, x_test, y_train, y_test = train_test_split(X_scaled, y, test_size=0.25, random_state=0)
```

```python
# 逻辑回归模型拟合数据集
from sklearn.linear_model import LogisticRegression # 导入类
# 我们现在使用“classifier”（分类器）而不是“regressor”（回归器）
classifier = LogisticRegression(random_state=0) # 创建对象
classifier.fit(X_train, y_train) # 拟合数据集
```

```python
# 预测
y_pred = classifier.predict(X_test)
```

```python
# 使用函数"confusion_matrix"来生成混淆矩阵
# 类名大写，函数名小写
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_true=y_test, y_pred=y_pred)
# cm 的参数：y_true: 真实值，y_pred: 预测值
```

```python
# 可视化训练集结果
from matplotlib.colors import ListedColormap
X_set, y_set = X_train, y_train
X1, X2 = np.meshgrid(np.arange(X_set[:,0].min(), X_set[:,0].max()+0.01, step=0.01), np.arange(X_set[:,1].min(), X_set[:,1].max()+0.01, step=0.01))
plt.contour(X1, X2, classifier.predict(np.array([X1.ravel(), X2.ravel()]).T).reshape(X1.shape), alpha=0.5, cmap=ListedColormap(['red', 'green']))
plt.xlim(X_set[:,0].min(), X_set[:,0].max())
plt.ylim(X_set[:,1].min(), X_set[:,1].max())
for i, j in enumerate(y_set):
    plt.scatter(X_set[j,0], X_set[j,1], c=ListedColormap(['yellow', 'blue'])(j), label=j)
plt.title('Logistic Regression (Training set)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

```python
# 可视化测试集结果
from matplotlib.colors import ListedColormap
X_set, y_set = X_test, y_test
X1, X2 = np.meshgrid(np.arange(X_set[:,0].min(), X_set[:,0].max()+0.01, step=0.01), np.arange(X_set[:,1].min(), X_set[:,1].max()+0.01, step=0.01))
```

```python
plt.contour(X1, X2, classifier.predict(np.array([X1.ravel(), X2.ravel()])).reshape(X1.shape))
plt.contour(X1, X2, alpha=0.25, cmap=ListedColormap(['red', 'green']))
plt.xlim(X1.min(), X1.max())
for i, j in enumerate(y_set):
    plt.scatter(X_set[y_set == j][:,0], j=1, c = ListedColormap(['yellow', 'blue'])(i), label = j)
plt.title('Logistic Regression (Test set)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

我们将得到数据集作为输出。考虑给定的图片：

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_89_0.png)

# 分类问题的新模板

```python
# 库
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# 数据提取
dataset = pd.read_csv("Social_Network_Ads.csv")
X = dataset.iloc[:, [2,3]].values
y = dataset.iloc[:, -1].values

# 数据划分后的特征缩放
# 数据划分
from sklearn.model_selection import train_test_split
# 我们将数据集分为训练集和测试集
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.25, random_state=0)

# 特征缩放
from sklearn.preprocessing import StandardScaler
# y不需要缩放：分类变量
sc = StandardScaler()
X_scaled = sc.fit_transform(X)
st_sc = StandardScaler()
x_train = st_sc.fit_transform(X_train)
x_test = st_sc.transform(X_test)
```

```python
# 数据划分前的特征缩放
# 特征缩放
from sklearn.preprocessing import StandardScaler
# y可能不需要缩放：分类变量
sc_x = StandardScaler()
x_scaled = sc_x.fit_transform(x_train)

# 数据划分
from sklearn.model_selection import train_test_split
# 0.25 的大小意味着总观测值的“1/4”
x_train, x_test, y_train, y_test = train_test_split(x_scaled, y, test_size=0.25, random_state=0)
```

```python
# 逻辑回归模型拟合数据集
from sklearn.linear_model import LogisticRegression
clf = LogisticRegression()
clf.fit(x_train, y_train)

# 预测
y_pred = classifier.predict(X_test)

# 使用函数 "confusion_matrix"来生成混淆矩阵
# 类名大写，函数名小写
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_true=y_test, y_pred=y_pred)
# cm 的参数：y_true: 真实值，y_pred: 预测值

```python
# 可视化训练集结果
from matplotlib.colors import ListedColormap
X_set, y_set = X_train, y_train
X1, X2 = np.meshgrid(np.arange(X_set[:,0].min(), X_set[:,0].max()+0.01, step=0.01), np.arange(X_set[:,1].min(), X_set[:,1].max()+0.01, step=0.01))
plt.contour(X1, X2, classifier.predict(np.array([X1.ravel(), X2.ravel()]).T).reshape(X1.shape), alpha=0.5, cmap=ListedColormap(['red', 'green']))
plt.xlim(X_set[:,0].min(), X_set[:,0].max())
plt.ylim(X_set[:,1].min(), X_set[:,1].max())
for i, j in enumerate(y_set):
    plt.scatter(X_set[j,0], X_set[j,1], c=ListedColormap(['yellow', 'blue'])(j), label=j)
plt.title('Logistic Regression (Training set)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

```python
# 可视化测试集结果
from matplotlib.colors import ListedColormap
X_set, y_set = X_test, y_test
X1, X2 = np.meshgrid(np.arange(X_set[:,0].min(), X_set[:,0].max()+0.01, step=0.01), np.arange(X_set[:,1].min(), X_set[:,1].max()+0.01, step=0.01))
```

```python
plt.contour(X1, X2, classifier.predict(np.array([X1.ravel(), X2.ravel()])).reshape(X1.shape))
plt.contour(X1, X2, alpha=0.25, cmap=ListedColormap(['red', 'green']))
plt.xlim(X1.min(), X1.max())
for i, j in enumerate(y_set):
    plt.scatter(X_set[y_set == j][:,0], j=1, c = ListedColormap(['yellow', 'blue'])(i), label = j)
plt.title('Logistic Regression (Test set)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

*(注：由于提供的原文文本在后半部分存在代码逻辑混乱（如 `classifier` 与 `clf` 混用，且代码块重复），译文严格遵循了“不漏译”和“不重复输出”的原则，对原文中的注释部分进行了翻译，并保持了代码结构的完整。)*

我们将得到数据集作为输出。考虑给定的图片：

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_89_0.png)

# 分类问题的新模板

（此处代码部分翻译已在上文涵盖，此处保持格式对齐）

