# 180 Introduction to python

the k-means model on the unlabeled dataset. In this section, the IRIS dataset is chosen to apply k_means on it. The reason for this selection is to visualize the clustering results and compare it with the real data. However, the class labels of samples are not utilized during the clustering algorithm. To evaluate the clustering algorithm in the real unlabeled dataset, the evaluation metrics like silhouette score, rank index, adjusted rank index, mutual information, and Davies-Bouldin index (Amigó, Gonzalo, Artiles, & Verdejo, 2009) are used. In the following, the python code to fit k-means on the IRIS dataset is given. Due to the visualization difficulty of high-dimensional data, first data is projected into a new space with two dimensions and then k-means is applied to it. It should be noted that the step of dimensionality reduction is not necessary for all clustering algorithms. In this example, it is done due to the visualization goal.

Like the previous two examples, in the first step, the necessary libraries should be imported as:

```
import numpy as np
from sklearn import datasets
from sklearn.decomposition import PCA
import matplotlib.pyplot as plt
Then, data and PCA is applied on it to project data into a new space with two dimensions as follows:
from sklearn.datasets import load_iris
data = load_iris()
from sklearn.decomposition import PCA
pca = PCA(n_components=2)
data_reduced = pca.fit_transform(data.data)
```

Next, k_means is applied on “data-reduced” variable:
from sklearn.cluster import KMeans
kmeans = KMeans(n_clusters=2, random_state=0).fit(data_reduced)

As is shown, by the “K_Means” class, an object from this class is constructed, and by calling the “fit” function for this object, clustering is done. The “K_Means” class gets two arguments where the first determines the number of clusters and the second determines how the centroids initialization is done. Now, the learned clusters are visualized as follows:

```
idx = np.argmax(kmeans.labels==0)
plt.scatter(data_reduced[idx,0],data_reduced[idx,1],color='blue')
idx = np.argmax(kmeans.labels==1)
```