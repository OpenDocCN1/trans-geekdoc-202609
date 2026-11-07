
欢迎来到层次聚类培训模块！本教程将为您提供对层次聚类技术的深入理解，探讨其原理、方法及应用。无论您是初学者还是希望加深知识，本指南都将帮助您掌握层次聚类的精髓。

# 1. 层次聚类简介

## 1.1. 什么是层次聚类？
层次聚类是一种聚类分析方法，旨在构建聚类的层次结构。与 `K-Means Clustering` 不同，后者需要预先指定聚类数量，层次聚类创建的是一种树状的聚类结构，可以在不同层级处切割以获得期望的聚类数量。

### 关键概念
● `Dendrogram`：一种树状图，显示聚类的排列方式以及聚类合并时的距离。
● `Agglomerative`：自底向上方法，每个数据点最初作为自己的聚类，随着向上移动层次结构而逐步合并聚类对。
● `Divisive`：自顶向下方法，所有数据点最初在一个聚类中，然后递归地将聚类拆分为更小的聚类。

## 1.2. 历史背景
层次聚类技术可以追溯到 1960 年代初期。特别是凝聚方法，由于其直观的树状结构，已在统计分析和数据挖掘中得到广泛使用。随着算法和计算方法的进步，层次聚类不断发展，成为各种数据分析任务中的标准工具。

# 2. 层次聚类的类型
层次聚类大致可分为两大类型：凝聚层次聚类和分裂层次聚类。

## 2.1. 凝聚层次聚类
`Agglomerative Hierarchical Clustering` (`AHC`) 是最常用的方法。它从每个数据点作为单独的聚类开始，并基于距离度量迭代合并聚类。

凝聚层次聚类的步骤：
1. 从单个点开始：每个数据点都是其自己的聚类。
2. 计算距离矩阵：计算每对聚类之间的距离。
3. 合并最近的聚类：将两个最近的聚类合并为一个聚类。
4. 更新距离矩阵：重新计算新聚类与剩余聚类之间的距离。
5. 重复：继续合并，直到所有数据点都属于一个聚类或达到期望的聚类数量。

凝聚聚类的示例可视化

![凝聚聚类](image_rsrcKCP.jpg)

图 1：凝聚层次聚类可视化

## 2.2. 分裂层次聚类
与凝聚聚类相比，分裂层次聚类是一种不太常见的方法。它从所有数据点在一个聚类中开始，并递归地将聚类拆分为更小的组。

分裂层次聚类的步骤：
1. 从所有点开始：所有数据点都在一个聚类中。
2. 拆分聚类：将聚类划分为两个或多个更小的聚类。
3. 更新距离矩阵：为新聚类重新计算距离。
4. 重复：继续拆分，直到达到期望的聚类数量。

## 2.3. 在凝聚聚类和分裂聚类之间选择
由于其简单性和有效性，凝聚聚类更为常用。然而，对于某些应用而言，如果自顶向下的方法更直观或更实用，则可能更倾向于使用分裂聚类。

# 3. 距离度量和连接标准

## 3.1. 距离度量
层次聚类依赖于距离度量来确定聚类之间的远近。常见的距离度量包括：
● `Euclidean Distance`：衡量特征空间中两点之间的直线距离。  
Distance=∑i=1n(xi−yi)2\\text{Distance} = \\sqrt{\\sum\_{i=1}^n (x\_i - y\_i)^2}Distance=∑i=1n​(xi​−yi​)2​
● `Manhattan Distance`：衡量两点沿垂直轴的距离。  
Distance=∑i=1n∣xi−yi∣\\text{Distance} = \\sum\_{i=1}^n |x\_i - y\_i|Distance=∑i=1n​∣xi​−yi​∣
● `Cosine Similarity`：衡量两个向量之间夹角的余弦，适用于文本数据。  
Cosine Similarity=x⋅y∥x∥∥y∥\\text{Cosine Similarity} = \\frac{x \\cdot y}{\\|x\\| \\|y\\|}Cosine Similarity=∥x∥∥y∥x⋅y​

## 3.2. 连接标准
连接标准决定了聚类之间距离的计算方式。常见的连接方法包括：
● `Single Linkage`：两个聚类中最近点之间的距离。  
d(A,B)=min⁡{d(a,b)∣a∈A,b∈B}d(A, B) = \\min \\{ d(a, b) \\mid a \\in A, b \\in B \\}d(A,B)=min{d(a,b)∣a∈A,b∈B}
● `Complete Linkage`：两个聚类中最远点之间的距离。  
d(A,B)=max⁡{d(a,b)∣a∈A,b∈B}d(A, B) = \\max \\{ d(a, b) \\mid a \\in A, b \\in B \\}d(A,B)=max{d(a,b)∣a∈A,b∈B}
● `Average Linkage`：两个聚类中所有点对之间的平均距离。  
d(A,B)=1∣A∣∣B∣∑a∈A∑b∈Bd(a,b)d(A, B) = \\frac{1}{|A||B|} \\sum\_{a \\in A} \\sum\_{b \\in B} d(a, b)d(A,B)=∣A∣∣B∣1​∑a∈A​∑b∈B​d(a,b)
● `Ward’s Linkage`：通过合并导致总类内方差最小增量的聚类来最小化聚类内的方差。

# 4. 层次聚类的实际应用

## 4.1. 客户细分
层次聚类用于根据购买行为、人口统计或其他特征对客户进行分组。这有助于企业定制营销策略并改善客户服务。

示例：
一家零售公司使用层次聚类将客户细分为频繁购买者、偶尔购买者和逛逛者等群体。

## 4.2. 基因表达分析
在生物信息学中，层次聚类用于分析基因表达数据，识别在不同条件下具有相似表达模式的基因。

示例：
研究人员使用层次聚类对在药物治疗下表现出相似表达谱的基因进行分组。

## 4.3. 文档聚类
层次聚类可用于对相似的文档、文章或网页进行分组，从而更轻松地组织大量文本数据。

示例：
新闻聚合器使用层次聚类将文章分类为政治、体育和娱乐等主题。

## 4.4. 图像分割
层次聚类有助于根据像素强度或颜色特征将图像分割为不同区域，这在图像处理任务中很有用。

示例：
计算机视觉应用使用层次聚类对医学图像中的感兴趣区域进行分割。

# 5. Python 中的层次聚类

## 5.1. 示例代码
以下是使用 `Scikit-Learn` 库在 Python 中执行凝聚层次聚类的实用示例：

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import AgglomerativeClustering
from sklearn.datasets import make_blobs
import scipy.cluster.hierarchy as sch

# Generate sample data
data, _ = make_blobs(n_samples=300, centers=4, cluster_std=0.60, random_state=0)

# Apply Agglomerative Hierarchical Clustering
clustering = AgglomerativeClustering(n_clusters=4, affinity='euclidean', linkage='ward')
labels = clustering.fit_predict(data)

# Plot the data points
plt.scatter(data[:, 0], data[:, 1], c=labels, cmap='viridis', marker='o', s=50)
plt.title('Agglomerative Hierarchical Clustering')
plt.xlabel('Feature 1')
plt.ylabel('Feature 2')
plt.show()

# Create a dendrogram
plt.figure(figsize=(10, 7))
dendrogram = sch.dendrogram(sch.linkage(data, method='ward'))
plt.title('Dendrogram')
plt.xlabel('Data Points')
plt.ylabel('Euclidean Distance')
plt.show()
```

代码说明：
1. 生成数据：创建包含 300 个样本和 4 个中心的合成数据。
