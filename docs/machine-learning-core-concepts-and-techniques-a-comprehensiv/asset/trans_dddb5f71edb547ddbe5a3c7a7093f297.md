

`y_pred = model.predict(X_test_scaled)`

# 评估模型

`accuracy = accuracy_score(y_test, y_pred)`

`conf_matrix = confusion_matrix(y_test, y_pred)`

`class_report = classification_report(y_test, y_pred)`

`print(f"Accuracy: {accuracy}")`

`print(f"Confusion Matrix:\\n{conf_matrix}")`

`print(f"Classification Report:\\n{class_report}")`

# 打印系数

```
for feature, coef in zip(X.columns, model.coef_[0]):
    print(f"{feature}: {coef}")
```

## 5.1.2 多分类逻辑回归

对于多分类问题，我们使用诸如一对多 OvR 或 softmax 回归等技术。

示例：预测鸢尾花种类

```python
from sklearn.datasets import load_iris
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, confusion_matrix, classification_report

# Load the iris dataset
iris = load_iris()
X = iris.data
y = iris.target

# Split the data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Create and train the model
model = LogisticRegression(multi_class='ovr')
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred)
conf_matrix = confusion_matrix(y_test, y_pred)
class_report = classification_report(y_test, y_pred, target_names=iris.target_names)

print(f"Accuracy: {accuracy}")
print(f"Confusion Matrix:\\n{conf_matrix}")
print(f"Classification Report:\\n{class_report}")
```

### 5.2 决策树

决策树是多功能的算法，可用于分类和回归任务。

## 5.2.1 决策树分类器

决策树分类器基于对输入特征的一系列问题做出决策。

示例：使用决策树预测客户流失

```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.tree import plot_tree
import matplotlib.pyplot as plt

# Create and train the model
model = DecisionTreeClassifier(max_depth=3, random_state=42)
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred)
conf_matrix = confusion_matrix(y_test, y_pred)
class_report = classification_report(y_test, y_pred)

print(f"Accuracy: {accuracy}")
print(f"Confusion Matrix:\\n{conf_matrix}")
print(f"Classification Report:\\n{class_report}")

# Visualize the tree
plt.figure(figsize=(20,10))
plot_tree(model, feature_names=X.columns, class_names=['No Churn', 'Churn'], filled=True, rounded=True)
plt.show()
```

## 5.2.2 决策树的优缺点

优点：

* 易于理解和解释
* 可以处理数值和分类数据
* 需要很少的数据准备

缺点：

* 可能创建过于复杂的树，导致泛化能力差
* 可能不稳定，因为数据中的微小变化可能导致完全不同的树

### 5.3 支持向量机 SVM

SVM 是一种强大且灵活的分类器，可在高维空间中找到最佳分离各类的超平面。

## 5.3.1 线性 SVM

线性 SVM 使用线性超平面来分离类别。

示例：使用线性 SVM 对鸢尾花进行分类

```python
from sklearn.svm import SVC
from sklearn.preprocessing import StandardScaler

# Scale the features
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Create and train the model
model = SVC(kernel='linear')
model.fit(X_train_scaled, y_train)

# Make predictions
y_pred = model.predict(X_test_scaled)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred)
conf_matrix = confusion_matrix(y_test, y_pred)
class_report = classification_report(y_test, y_pred, target_names=iris.target_names)

print(f"Accuracy: {accuracy}")
print(f"Confusion Matrix:\\n{conf_matrix}")
print(f"Classification Report:\\n{class_report}")
```

## 5.3.2 非线性 SVM

非线性 SVM 使用核技巧将输入空间转换到更高维空间，使类别变得线性可分。

示例：使用 RBF 核的 SVM 对鸢尾花进行分类

```python
# Create and train the model
model = SVC(kernel='rbf')
model.fit(X_train_scaled, y_train)

# Make predictions
y_pred = model.predict(X_test_scaled)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred)
conf_matrix = confusion_matrix(y_test, y_pred)
class_report = classification_report(y_test, y_pred, target_names=iris.target_names)

print(f"Accuracy: {accuracy}")
print(f"Confusion Matrix:\\n{conf_matrix}")
print(f"Classification Report:\\n{class_report}")
```

### 5.4 k-最近邻 k-NN

k-NN 是一种简单、基于实例的学习算法，根据其 k 个最近邻居的多数类别对数据点进行分类。

示例：使用 k-NN 对鸢尾花进行分类

```python
from sklearn.neighbors import KNeighborsClassifier

# Create and train the model
model = KNeighborsClassifier(n_neighbors=3)
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred)
conf_matrix = confusion_matrix(y_test, y_pred)
class_report = classification_report(y_test, y_pred, target_names=iris.target_names)

print(f"Accuracy: {accuracy}")
print(f"Confusion Matrix:\\n{conf_matrix}")
print(f"Classification Report:\\n{class_report}")
```

## 5.4.1 选择合适的 k

k 的选择会显著影响 k-NN 的性能。我们可以使用交叉验证来找到最佳的 k。

```python
from sklearn.model_selection import cross_val_score

k_range = range(1, 31)
k_scores = []

for k in k_range:
    knn = KNeighborsClassifier(n_neighbors=k)
    scores = cross_val_score(knn, X_train, y_train, cv=5, scoring='accuracy')
    k_scores.append(scores.mean())

plt.plot(k_range, k_scores)
plt.xlabel('Value of K')
plt.ylabel('Cross-Validated Accuracy')
plt.show()
```

### 5.5 朴素贝叶斯

朴素贝叶斯分类器是一类基于在特征之间施加强独立性假设的应用贝叶斯定理的简单概率分类器。

## 5.5.1 高斯朴素贝叶斯

高斯朴素贝叶斯假设特征服从正态分布。

示例：使用高斯朴素贝叶斯对鸢尾花进行分类

```python
from sklearn.naive_bayes import GaussianNB

# Create and train the model
model = GaussianNB()
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred)
conf_matrix = confusion_matrix(y_test, y_pred)
class_report = classification_report(y_test, y_pred, target_names=iris.target_names)

print(f"Accuracy: {accuracy}")
print(f"Confusion Matrix:\\n{conf_matrix}")
print(f"Classification Report:\\n{class_report}")
```

## 5.5.2 多项式朴素贝叶斯

多项式朴素贝叶斯常用于文本分类。

示例：使用多项式朴素贝叶斯进行文本分类

```python
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.naive_bayes import MultinomialNB
from sklearn.model_selection import train_test_split

# Sample text data
texts = ["This is a positive review", "Negative sentiment here", "I love this product", "Terrible experience", "Great service"]
labels = [1, 0, 1, 0, 1]  # 1 for positive, 0 for negative

# Prepare the data
vectorizer = CountVectorizer()
X = vectorizer.fit_transform(texts)
X_train, X_test, y_train, y_test = train_test_split(X, labels, test_size=0.2, random_state=42)

# Create and train the model
model = MultinomialNB()
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)
```

