# 6.4 KNN regression

K nearest neighbors (KNN) regression is an example of a nonparametric model, in which for a given query data point q, we find its k nearest neighbors in the training set and compute the average response variable y. In this section, we'll compute the average of KNN target labels for the iris dataset. The average is taken over the local neighborhood of K points that are closest to our query q.

$y_q = \frac{1}{K} \sum_{i \in N_K(q,D)} y_i \quad (6.11)$

Here, $N_K(q, D)$ denotes the local neighborhood of $k$ nearest neighbors to query $q$ from the training dataset $D$. To find the local neighborhood $N_K(q, D)$, we can compute a distance between the query point $q$ and each of the training dataset points $x_i \in D$, sort these distances in ascending order, and take the top $K$ data points. The runtime complexity of this approach is $O(n \log n)$, where $n$ is the size of the training dataset due to the sort operation. We are now ready to implement a KNN regressor from scratch! In figure 6.6, KNN regression is computed by averaging the labels of K nearest neighbors based on Euclidean distance.

```
1: class KNN:
2: function knn_search(K, X, y, Q)
3: for query in Q:
4:   idx = argsort(euclidian_dist(query, X))[:K] ← KNN IDs
5:   knn_labels = [y[i] for i in idx] ← KNN labels
6:   y_pred = mean(knn_labels) ← KNN regression
7: end for
8: return y_pred
```

Figure 6.6 KNN regression pseudo-code

The code consists of the knn_search function, in which for every K nearest neighbor query Q, we compute the Euclidean distance between the query and all of the data points, sort the results, and pick out K lowest distance IDs. We then form the KNN region by collecting the labels with KNN IDs. Finally, we compute our result by averaging over KNN labels.

# Listing 6.3 K nearest neighbors regression

```
import numpy as np
import matplotlib.pyplot as plt

from sklearn import datasets
from sklearn.model_selection import train_test_split

np.random.seed(42)
```