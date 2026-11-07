
Welcome to the training module on Hierarchical Clustering! This tutorial will provide you with an in-depth understanding of hierarchical clustering techniques, exploring its principles, methods, and applications. Whether you're a beginner or looking to deepen your knowledge, this guide will help you master the art of hierarchical clustering.

# 1. Introduction to Hierarchical Clustering

## 1.1. What is Hierarchical Clustering?
Hierarchical Clustering is a method of cluster analysis that seeks to build a hierarchy of clusters. Unlike `K-Means Clustering`, which requires you to specify the number of clusters in advance, hierarchical clustering creates a tree-like structure of clusters, which can be cut at various levels to achieve the desired number of clusters.

### Key Concepts
● `Dendrogram`: A tree diagram that shows the arrangement of clusters and the distances at which clusters are merged.
● `Agglomerative`: A bottom-up approach where each data point starts as its own cluster, and pairs of clusters are merged as you move up the hierarchy.
● `Divisive`: A top-down approach where all data points start in one cluster, and the cluster is recursively split into smaller clusters.

## 1.2. Historical Background
Hierarchical clustering techniques date back to the early 1960s. The agglomerative approach, in particular, has been widely used in statistical analysis and data mining due to its intuitive tree structure. Over time, hierarchical clustering has evolved with advancements in algorithms and computational methods, becoming a standard tool in various data analysis tasks.

# 2. Types of Hierarchical Clustering
Hierarchical clustering can be broadly categorized into two main types: Agglomerative Hierarchical Clustering and Divisive Hierarchical Clustering.

## 2.1. Agglomerative Hierarchical Clustering
`Agglomerative Hierarchical Clustering` (`AHC`) is the most commonly used approach. It starts with each data point as an individual cluster and merges clusters iteratively based on a distance metric.

Steps in Agglomerative Hierarchical Clustering:
1. Start with Individual Points: Each data point is its own cluster.
2. Compute Distance Matrix: Calculate the distances between each pair of clusters.
3. Merge Closest Clusters: Combine the two closest clusters into a single cluster.
4. Update Distance Matrix: Recompute the distances between the new cluster and the remaining clusters.
5. Repeat: Continue merging until all data points are in one cluster or the desired number of clusters is reached.

Example Visualization of Agglomerative Clustering

![Agglomerative Clustering](image_rsrcKCP.jpg)

Figure 1: Agglomerative Hierarchical Clustering Visualization

## 2.2. Divisive Hierarchical Clustering
Divisive Hierarchical Clustering is a less common approach compared to agglomerative clustering. It starts with all data points in one cluster and recursively splits the clusters into smaller groups.

Steps in Divisive Hierarchical Clustering:
1. Start with All Points: All data points are in one cluster.
2. Split Clusters: Divide the cluster into two or more smaller clusters.
3. Update Distance Matrix: Recalculate distances for the new clusters.
4. Repeat: Continue splitting until the desired number of clusters is achieved.

## 2.3. Choosing Between Agglomerative and Divisive Clustering
Agglomerative clustering is more commonly used due to its simplicity and effectiveness. However, divisive clustering might be preferred for certain applications where a top-down approach is more intuitive or practical.

# 3. Distance Metrics and Linkage Criteria

## 3.1. Distance Metrics
Hierarchical clustering relies on distance metrics to determine how close or far apart clusters are. Common distance metrics include:
● `Euclidean Distance`: Measures the straight-line distance between two points in the feature space.  
Distance=∑i=1n(xi−yi)2\\text{Distance} = \\sqrt{\\sum\_{i=1}^n (x\_i - y\_i)^2}Distance=∑i=1n​(xi​−yi​)2​
● `Manhattan Distance`: Measures the distance between two points along axes at right angles.  
Distance=∑i=1n∣xi−yi∣\\text{Distance} = \\sum\_{i=1}^n |x\_i - y\_i|Distance=∑i=1n​∣xi​−yi​∣
● `Cosine Similarity`: Measures the cosine of the angle between two vectors, useful for text data.  
Cosine Similarity=x⋅y∥x∥∥y∥\\text{Cosine Similarity} = \\frac{x \\cdot y}{\\|x\\| \\|y\\|}Cosine Similarity=∥x∥∥y∥x⋅y​

## 3.2. Linkage Criteria
Linkage criteria determine how the distance between clusters is calculated. Common linkage methods include:
● `Single Linkage`: Distance between the closest points of the two clusters.  
d(A,B)=min⁡{d(a,b)∣a∈A,b∈B}d(A, B) = \\min \\{ d(a, b) \\mid a \\in A, b \\in B \\}d(A,B)=min{d(a,b)∣a∈A,b∈B}
● `Complete Linkage`: Distance between the farthest points of the two clusters.  
d(A,B)=max⁡{d(a,b)∣a∈A,b∈B}d(A, B) = \\max \\{ d(a, b) \\mid a \\in A, b \\in B \\}d(A,B)=max{d(a,b)∣a∈A,b∈B}
● `Average Linkage`: Average distance between all pairs of points in the two clusters.  
d(A,B)=1∣A∣∣B∣∑a∈A∑b∈Bd(a,b)d(A, B) = \\frac{1}{|A||B|} \\sum\_{a \\in A} \\sum\_{b \\in B} d(a, b)d(A,B)=∣A∣∣B∣1​∑a∈A​∑b∈B​d(a,b)
● `Ward’s Linkage`: Minimizes the variance within clusters by merging clusters that result in the smallest increase in total within-cluster variance.

# 4. Practical Applications of Hierarchical Clustering

## 4.1. Customer Segmentation
Hierarchical Clustering is used to group customers based on purchasing behavior, demographics, or other features. This helps businesses tailor marketing strategies and improve customer service.

Example:
A retail company uses hierarchical clustering to segment customers into groups such as frequent buyers, occasional buyers, and window shoppers.

## 4.2. Gene Expression Analysis
In bioinformatics, hierarchical clustering is used to analyze gene expression data, identifying genes with similar expression patterns across different conditions.

Example:
A researcher uses hierarchical clustering to group genes that exhibit similar expression profiles in response to a drug treatment.

## 4.3. Document Clustering
Hierarchical Clustering can be applied to group similar documents, articles, or web pages, making it easier to organize large collections of text data.

Example:
A news aggregator uses hierarchical clustering to categorize articles into topics like politics, sports, and entertainment.

## 4.4. Image Segmentation
Hierarchical Clustering helps segment images into different regions based on pixel intensity or color features, which is useful in image processing tasks.

Example:
A computer vision application uses hierarchical clustering for segmenting regions of interest in medical images.

# 5. Hierarchical Clustering in Python

## 5.1. Example Code
Here’s a practical example demonstrating how to perform Agglomerative Hierarchical Clustering in Python using the `Scikit-Learn` library:

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

Code Explanation:
1. Generate Data: Create synthetic data with 300 samples and 4 centers.
