```
Python
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

# Social network analysis using spectral clustering

![](bbox=[0.11, 0.5, 0.46, 0.73])

Spectral clustering can group people according to social networks

Spectral clustering may be useful in contexts such as social network analysis to identify communities within networks by treating nodes as people and edges as their relationships.

> > See also
> Reference the scikit-learn documentation for spectral clustering by searching online for scikit-learn's section 2.3.5 "Spectral clustering" (https://scikit-learn.org/stable/modules/clustering.html#spectral-clustering).

# Hierarchical clustering

This approach builds a tree of clusters and doesn't require the number of clusters to be specified in advance. It provides a dendrogram (a tree-like diagram) to interpret the data by viewing at different levels of granularity, however, it is computationally intensive for large data sets.