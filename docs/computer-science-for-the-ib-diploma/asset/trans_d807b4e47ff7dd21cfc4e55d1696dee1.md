

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import make_moons
from sklearn.neighbors import kneighbors_graph
from sklearn.cluster import SpectralClustering
# Generate synthetic data (two interleaving half circles)
x, _ = make_moons(n_samples=300, noise=0.07, random_state=42)
# Create a k-nearest neighbours graph
knn_graph = kneighbors_graph(x, n_neighbors=10, include_self=False,
mode="distance")
# Apply spectral clustering using the KNN graph
spectral = SpectralClustering(n_clusters=2, affinity="precomputed",
assign_labels="kmeans", random_state=42)
labels = spectral.fit_predict(knn_graph)
# Plot the results
plt.figure(figsize=(8, 4))
plt.scatter(x[:, 0], x[:, 1], c=labels, cmap=plt.cm.rainbow, edgecolor="k", s=50)
plt.title("Spectral Clustering results")
plt.xlabel("Feature 0")
plt.ylabel("Feature 1")
plt.show()
```

## 基于光谱聚类的社交网络分析

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_248_0.png)

Spectral clustering can group people according to social networks

Spectral clustering may be useful in contexts such as social network analysis to identify communities within networks by treating nodes as people and edges as their relationships.

> > 另请参阅
> 要查找 scikit-learn 关于光谱聚类的文档，请在线搜索 scikit-learn 的第 2.3.5 节“光谱聚类”（https://scikit-learn.org/stable/modules/clustering.html#spectral-clustering）。

## 层次聚类

This approach builds a tree of clusters and doesn't require the number of clusters to be specified in advance. It provides a dendrogram (a tree-like diagram) to interpret the data by viewing at different levels of granularity, however, it is computationally intensive for large data sets.

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_249_0.png)

Example applications include genealogy research to analyse genetics to understand family relationships, and organizing library resources such as books and journals in a manner that reflects similarity of content based on topics, themes or authors.

In this plot of a family tree, individuals from the same family are grouped closer together first and, as you move up the dendrogram, families start merging based on their similarities (distances).

- Hierarchical clustering tree

> **另请参阅**
> 
> 要查找带有树状图的 scikit-learn 层次聚类文档，请在线搜索 scikit-learn 的“绘制层次聚类树状图”（https://scikit-learn.org/stable/auto_examples/cluster/plot_agglomerative_dendrogram.html）。

## DBSCAN 聚类

> **关键信息**
> 
> DBSCAN stands for Density-Based Spatial Clustering of Applications with Noise.

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_249_1.png)

DBSCAN clustering will group together points that are close to each other based on a distance measurement and a minimum number of points. It is very effective for data with clusters of similar density. Unlike k-means, DBSCAN does not require the number of clusters to be specified. It can find arbitrarily shaped clusters and can handle noise and outliers.

An example application might be to detect fraudulent financial transactions by clustering on similarities of amount, location and time. DBSCAN can identify the dense clusters that are “typical” and then separate out unusual transactions for alerts.

- Density-based spatial clustering

> **另请参阅**
> 
> 要查找 scikit-learn 的 DBSCAN 文档，请在线搜索 scikit-learn 的第 2.3.7 节“DBSCAN”（https://scikit-learn.org/stable/modules/clustering.html#dbscan）。

> **关联规则：**
> 在数据中查找共现模式的过程；这意味着，给定记录中存在某一项，另一项存在的可能性有多大。

## A4.3.5 无监督学习：关联规则

The association rule can be understood as a data mining technique that seeks to find co-occurrences within a data set. It is another form of unsupervised learning. The technique is commonly applied for market analysis, as well as crime analysis, healthcare, web / app behaviour tracking, and more.

There are three key metrics associated with association rule learning:

- Support: The proportion of transactions that include a particular item or combination of items.
- Confidence: The likelihood of occurrence of a particular item (B) when given some other item (A).
- Lift: The degree to which two items will appear together in this model, compared to the expected likelihood of them appearing together if the items were statistically independent; a lift value greater than 1 indicates the presence of item A increases the likelihood of B appearing.

The following example uses a data set of transactions from a fresh food market to find the items that are frequently purchased together. You can download the data set from https://github.com/paulbaumgarten/hodder-ibdp-computerscience

The first table, frequent itemsets, shows the support value for each set of items. In this case, 84 per cent of transactions include the sale of Milk. The association rules table illustrates the association between the antecedent (prerequisite) item and the consequent (resulting) item. In this case, the table shows:

- 62 per cent of transactions involve both Milk and Bread
- there is a 73 per cent likelihood that the customer will also purchase Bread if they purchase Milk
- the lift of 1.05 indicates that Bread is 1.05 times more likely to be purchased with Milk than without it.

| 支持度 | 项集 |
|---|---|
| 0.84 | (Milk) |
| 0.70 | (Bread) |
| 0.60 | (Butter) |
| 0.60 | (Egg) |
| 0.54 | (Cheese) |
| ... | ... |
| 0.40 | (Pasta, Butter, Bacon, Chicken) |
| 0.40 | (Apple, Banana, Coffee, Chicken) |
| 0.40 | (Apple, Banana, Bacon, Coffee) |
| 0.42 | (Banana, Bacon, Coffee, Chicken) |
| 0.40 | (Pasta, Banana, Bacon, Chicken) |

| 前项 | 后项 | 支持度 | 置信度 | 提升度 |
|---|---|---|---|---|
| (Milk) | (Bread) | 0.62 | 0.738095 | 1.054422 |
| (Bread) | (Milk) | 0.62 | 0.885714 | 1.054422 |
| (Butter) | (Milk) | 0.50 | 0.833333 | 0.992063 |
| (Egg) | (Milk) | 0.50 | 0.833333 | 0.992063 |
| (Cheese) | (Milk) | 0.50 | 0.925926 | 1.102293 |
| ... | ... | ... | ... | ... |
| (Pasta, Bacon) | (Banana, Chicken) | 0.40 | 0.833333 | 1.602564 |
| (Pasta, Chicken) | (Banana, Bacon) | 0.40 | 0.740741 | 1.322751 |
| (Banana, Bacon) | (Pasta, Chicken) | 0.40 | 0.714286 | 1.322751 |
| (Banana, Chicken) | (Pasta, Bacon) | 0.40 | 0.765211 | 1.602564 |
| (Bacon, Chicken) | (Pasta, Banana) | 0.40 | 0.714286 | 1.552795 |

```python
import pandas as pd
from mlxtend.preprocessing import TransactionEncoder
from mlxtend.frequent_patterns import apriori, association_rules
# Load data set
df = pd.read_csv("biased_transactions.csv")
# Generate frequent itemsets
frequent_itemsets = apriori(df, min_support=0.4, use_colnames=True)
# Generate association rules
rules = association_rules(frequent_itemsets, metric="confidence", min_threshold=0.7)
# Display the results
print("Frequent Itemsets:")
print(frequent_itemsets)
print("Association Rules:")
print(rules[["antecedents", "consequents", "support", "confidence", "lift"]])
```

This example uses an algorithm called Apriori in the mlxtend library for discovering the frequent data sets. Here is a high-level overview of the Apriori algorithm:

- Determine a threshold for the minimum level of support that will be considered (40 per cent in the code example above).
- Identify individual items in the data set that meet the threshold and store their appearance count.
- Progress to identifying pairs of items and larger groupings of items in the data set that also meet the minimum threshold.
- If a set of items does not meet the threshold at a small level, it can be removed from further consideration.
- The result is all combinations of items that appear frequently together or at or above the minimum threshold.

> **另请参阅**
> 要查找关联规则处理的 mlxtend 文档，请在线搜索 mlxtend 关联规则处理文档（https://rasbt.github.io/mlxtend/user_guide/frequent_patterns/association_rules）。

## A4.3.6 增强学习

Previously, "reinforcement learning" was described as learning from trial and error. In that vein, it can be likened to a toddler learning to walk. Every time the toddler falls over, they learn a little more about how to correctly balance themselves next time, until they eventually become a stable and confident walker.

