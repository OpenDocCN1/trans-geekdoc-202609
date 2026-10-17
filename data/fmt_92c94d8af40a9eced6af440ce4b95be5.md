
# 加载鸢尾花数据集

```python
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
df['species'] = iris.target
print(df.head())
```

## 第 3 步：将数据分为训练集和测试集

```python
### 定义特征 (X) 和目标变量 (y)
X = df.iloc[:, :-1]
y = df['species']
### 将数据分为 80% 训练集和 20% 测试集
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

## 第 4 步：训练 SVM 模型

```python
# 初始化并训练 SVM 模型
svm_model = SVC(kernel='linear', C=1.0)
svm_model.fit(X_train, y_train)
```

## 第 5 步：进行预测

```python
### 在测试数据进行预测
y_pred = svm_model.predict(X_test)
print("Predicted Labels:", y_pred)
```

## 调整 SVM 超参数

为了提高模型性能，我们可以微调超参数，如核类型、正则化参数（`C`）和 `gamma`。

1. 核技巧（Kernel Trick）：核函数将输入数据映射到高维空间，使其变得线性可分。常见的核包括：

   - 线性核（Linear Kernel）：适用于线性可分的数据。
   - 多项式核（Polynomial Kernel）：适用于具有多项式决策边界的数据集。
   - 径基函数核（RBF Kernel）：适用于复杂的非线性可分的数据集。

2. 正则化参数（`C`）：控制在最大化间隔和允许分类错误之间的权衡。高 `C` 值会导致分类错误减少，但可能会过拟合；而低 `C` 值则会导致更软的间隔（softer margin）。

3. `Gamma` 参数：决定单个训练样本的影响力。低 `gamma` 值会考虑远离超平面的点，而高 `gamma` 值则关注靠近的点。

### 使用 GridSearchCV 实现超参数调优

```python
from sklearn.model_selection import GridSearchCV
# 定义参数网格
param_grid = {'C': [0.1, 1, 10], 'kernel': ['linear', 'rbf', 'poly'], 'gamma': [0.1, 1]}
### 初始化 GridSearch
grid_search = GridSearchCV(SVC(), param_grid, cv=5)
grid_search.fit(X_train, y_train)
### 显示最佳参数
print("Best Parameters:", grid_search.best_params_)
```

## 示例：使用 SVM 分类花

```python
# 可视化结果
sns.scatterplot(data=df, x='sepal_length', y='sepal_width', hue='species')
plt.xlabel('Sepal Length (cm)')
plt.ylabel('Sepal Width (cm)')
plt.title('Iris Classification')
plt.show()
```

（注：提供的文本包含大量重复和乱码部分。我已经根据提供的标准 SVM 工作流上下文清理了逻辑。）

```python
best_k = 5  # 假设使用手部法找到了最佳 K

knn = KNeighborsClassifier(n_neighbors=best_k)

knn.fit(X_train, y_train)
```

### 预测

```python
y_pred = knn.predict(X_test)
```

# 性能指标

```python
print("Confusion Matrix:\n", confusion_matrix(y_test, y_pred))
print("Classification Report:\n", classification_report(y_test, y_pred))
```

混淆矩阵提供了正确预测和错误预测的详细分类，而分类报告则包含了精确率、召回率和 F1 分数。

## 示例：使用 KNN 对手写数字分类

`digits` 数据集包含手写数字（0-9）的图像，我们可以使用 KNN 根据像素强度对它们进行分类。

### 步骤 1：加载并可视化数据集

```python
import matplotlib.pyplot as plt
import numpy as np
from sklearn.datasets import load_digits

### 加载数据集
digits = load_digits()

# 显示样本图像
fig, axes = plt.subplots(1, 10, figsize=(10, 3))
for i in range(10):
    axes[i].imshow(digits.images[i], cmap='gray')
    axes[i].set_title(digits.target[i])
    axes[i].axis('off')
plt.show()
```

### 步骤 2：训练 KNN 模型

```python
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier

### 划分数据集
X_train, X_test, y_train, y_test = train_test_split(digits.data, digits.target, test_size=0.2, random_state=42)

# 训练
knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(X_train, y_train)

### 预测
y_pred = knn.predict(X_test)
```

### 步骤 3：评估模型

```python
from sklearn.metrics import accuracy_score

### 计算准确率
accuracy = accuracy_score(y_test, y_pred)
print(f"KNN Accuracy on Handwritten Digits Dataset: {accuracy:.2f}")
```

### 步骤 4：可视化预测

```python
fig, axes = plt.subplots(1, 5, figsize=(10, 3))
for i in range(5):
    axes[i].imshow(X_test[i].reshape(8, 8), cmap='gray')
    axes[i].set_title(f"Pred: {y_pred[i]}")
    axes[i].axis('off')
plt.show()
```

这种可视化有助于验证模型是否正确分类了手写数字。

# 第 1 天：聚类引言

聚类（Clustering）是机器学习中的一种无监督学习，根据相似性对数据点进行分组。与需要标签的分类不同，聚类算法通过识别模式和形成聚类来发现数据集中的内在结构。

聚类广泛应用于各个行业，用于市场细分、异常检测等。最流行的聚类技术是 K-Means 聚类和层次聚类。

## K-Means 聚类

K-Means 聚类由于其简单高效，是最广泛广泛的算法之一。它将数据集划分为 `K` 个不同的、不重叠的簇，每个数据点都属于与其均值最近的簇。

### K-Means 工作原理：

1. 在数据空间内随机初始化 `K` 个质心。
2. 根据欧式距离将每个数据点分配给最近的质心。
3. 通过计算分配给每个簇的所有点的平均来重新计算质心。
4. 重复步骤 2-3，直到质心不再变化或达到预定义的迭代限制。

### 在 Python 中实现 K-Means

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
from sklearn.datasets import make_blobs

### 生成合成数据集
X, y = make_blobs(n_samples=300, centers=4, cluster_std=0.6, random_state=42)

# 应用 K-Means 聚类
kmeans = KMeans(n_clusters=4, random_state=42)
kmeans.fit(X)
labels = kmeans.labels_
centroids = kmeans.cluster_centers_

# 可视化聚类结果
plt.scatter(X[:, 0], X[:, 1], c=labels, cmap='viridis', alpha=0.6)
plt.scatter(centroids[:, 0], centroids[:, 1], marker='X', s=200, c='red', label='Centroids')
plt.title("K-Means Clustering")
plt.legend()
plt.show()
```

### 层次聚类

与 K-Means 不同，层次聚类可以在不指定簇数量的情况下创建层次结构。主要有两种：

1. **凝聚聚类（Agglomerative Clustering，自底而上）：**

   - 每个数据点开始作为一个簇。
   - 根据相似性迭代合并簇。
   - 过程持续直到所有数据点聚为一个一类。

2. **分裂聚类（Divisive Clustering，自顶而下）：**

   - 从包含所有数据点的单一大簇开始。
   - 迭代地将簇分成更小的子簇。
   - 过程直到每个数据点都是自己的簇。

### 在 Python 中实现层次聚类

```python
from scipy.cluster.hierarchy import dendrogram, linkage
from sklearn.cluster import AgglomerativeClustering

# 计算层次连接
linked = linkage(X, method='ward')

# 绘制树图
plt.figure(figsize=(10, 5))
dendrogram(linked)
plt.title("Hierarchical Clustering Dendrogram")
plt.xlabel("Data Points")
plt.ylabel("Distance")
plt.show()
```

## 聚类的现实世界应用

聚类应用于许多领域，帮助组织从数据中获取意义的见解。常见应用包括：

1. **营销中的客户细分**

   - 根据购买行为、人口统计数据或偏好对客户进行分组。
   - 有助于目标广告和个性化营销活动。

2. **网络安全中的异常检测**

   - 通过检测网络流量中的异常行为识别欺诈活动或安全威胁。
   - 用于金融欺诈、垃圾邮件过滤和网络入侵检测。

3. **文档分类与主题建模**

   - 将相似的文章、研究论文或新闻内容归类，便于检索。
   - 用于推荐系统和搜索引擎。

4. **医学诊断与疾病检测**

   - 根据症状和病史对患者数据进行聚类，以识别疾病模式。
   - 有助于诊断罕见病。

# 第 13 天：朴素贝叶斯分类器简介

## 理解概率分类

在机器学习中，概率分类是一种通过模型预测给定数据实例属于特定类别的概率的方法。这与通过简单分配标签来进行硬分类（hard classifications）的传统分类器不同。朴素贝叶斯（Naïve Bayes）是一种基于贝叶斯定理的概率分类器，它根据相关条件的先验知识来计算事件发生的几然。

![C:\Users\anike\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\4EDC598.tmp](img/image_rsrc40F.jpg)

### 什么是贝叶斯定理？

贝叶斯定理是朴素贝叶斯分类的数学基础，表达式为：

![](img/image_rsrc40G.jpg)

其中：

- `P(A|B)`: 在给定证据 B 的情况下，类别 A 的概率（后验概率）。
- `P(B|A)`: 在给定类别 A 的情况下，证据 B 的概率。
- `P(A)`: 类别 A 的先验概率。
- `P(B)`: 证据 B 发生的概率。

朴素贝叶斯假设特征之间是条件独立的，这意味着一个特征的存在不会影响另一个特征的概率。这种假设虽然是不符合实际的，但它让计算变得更快、更高效。

# 实现用于文本分类的朴素贝叶斯

朴素贝叶斯广泛用于文本分类，特别是垃圾邮件过滤、情感分析和文档分类。它对于传统模型难以处理的高维数据尤为有效。

### 第 1 步：导入所需的库

```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.feature_extraction.text import CountVectorizer, TfidfTransformer
from sklearn.naive_bayes import MultinomialNB
from sklearn.metrics import accuracy_score, classification_report
```

### 第 2 步：示例数据集 – 电影评论

```python
# 电影评论示例数据集
reviews = [
    "This movie was fantastic! I loved the characters and story.",
    "Terrible film. Worst acting and plot I have ever seen.",
    "Absolutely amazing! A must-watch for all action lovers.",
    "The movie was dull, boring, and predictable. Waste of time.",
    "Brilliant cinematography and great performances!",
    "Horrible! The script was awful and full of clichés.",
    "One of the best movies I have seen this year.",
    "Not worth watching. I regret buying the ticket.",
    "Outstanding performance by the lead actor!",
    "Disappointing. Poor direction and weak storyline."
]
labels = [1, 0, 1, 0, 1, 0, 1, 0, 1, 0]  # 1: 正性，0: 负性
```

### 第 3 步：文本预处理

```python
# 将文本转换为数值特征向量
vectorizer = CountVectorizer(stop_words='english')
X_counts = vectorizer.fit_transform(reviews)

### 应用 TF-IDF 转换
tfidf_transformer = TfidfTransformer()
X_tfidf = tfidf_transformer.fit_transform(X_counts)
```

### 第 4 步：训练朴素贝叶斯分类器

```python
# 分割数据集
X_train, X_test, y_train, y_test = train_test_split(X_tfidf, labels, test_size=0.2, random_state=42)

# 训练多项式朴素贝叶斯模型
nb_model = MultinomialNB()
nb_model.fit(X_train, y_train)
```

### 第 5 步：预测与评估性能

```python
### 在测试集上预测
y_pred = nb_model.predict(X_test)

### 计算准确率
accuracy = accuracy_score(y_test, y_pred)
print(f"朴素贝叶斯准确率: {accuracy:.2f}")

### 显示分类报告
print("分类报告:\n", classification_report(y_test, y_pred))
```

朴素贝叶斯在文本应用中表现出色，是它最常用的分类器之一。

# 朴素贝叶斯的优点与缺点

### 优点：

- **快速高效**：训练时间短，且在大数据集上表现良好。
- **在高维数据上表现良好**：适用于文本分类。
- **简单易于解释**：易于实现和解释结果。
- **对无关特征具有鲁棒性**：在处理文本分类中的词袋模型噪声数据集时表现很好。

### 缺点：

- **强独立性假设**：假设所有特征都是独立的，这在现实世界数据中很少成立。
- **对连续数据局限**：最适用于类别或文本数据；连续数据需要使用高斯朴素贝叶斯。
- **在小数据集上困难**：需要足够的训练数据来产生可靠的概率估计。

# 示例：将电影评论分类为正性或负性

让我们在新的电影评论上测试分类器。
