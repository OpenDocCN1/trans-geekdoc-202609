
|   |   |   |   |   |   |
|---|---|---|---|---|---|
| 3 | Calais | 3175 | 1326 | 204 | 0 |
| 4 | Cherbourg | 3339 | 1294 | 583 | 460 |

Recover coordinates of the cities in Euclidean referential whose orientation is arbitrary:

```
from sklearn import metrics
Deuclidean = metrics.pairwise.pairwise_distances(X, metric='euclidean')
print(np.round(Deuclidean[:5, :5]))
```

```
[[ 0. 3116. 2994. 3181. 3428.]
[3116. 0. 1317. 1289. 1128.]
[2994. 1317. 0. 198. 538.]
[3181. 1289. 198. 0. 358.]
[3428. 1128. 538. 358. 0.]]
```

Plot the results:

```
# Plot: apply some rotation and flip
theta = 80 * np.pi / 180.
rot = np.array([[np.cos(theta), -np.sin(theta)],
                [np.sin(theta),  np.cos(theta)]])
Xr = np.dot(X, rot)
# flip x
Xr[:, 0] *= -1
plt.scatter(Xr[:, 0], Xr[:, 1])

for i in range(len(city)):
    plt.text(Xr[i, 0], Xr[i, 1], city[i])
plt.axis('equal')
```

```
(-1894.1017744377398,
2914.3652937179477,
-1712.9885463201906,
2145.4522453884565)
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_157_0.png)

### 10.4.3 Determining the number of components

We must choose $K^* \in \{1,\dots,K\}$ the number of required components. Plotting the values of the stress function, obtained using $k \le N - 1$ components. In general, start with $1,\dots,K \le 4$. Choose $K^*$ where you can clearly distinguish an *elbow* in the stress curve.

Thus, in the plot below, we choose to retain information accounted for by the first *two* components, since this is where the *elbow* is in the stress curve.

```
k_range = range(1, min(5, D.shape[0]-1))
stress = [MDS(dissimilarity='precomputed', n_components=k,
    random_state=42, max_iter=300, eps=1e-9).fit(D).stress_ for k in k_range]

print(stress)
plt.plot(k_range, stress)
plt.xlabel("k")
plt.ylabel("stress")
```

```
[48644495.28571428, 3356497.365752386, 2858455.495887962, 2756310.637628011]
```

```
Text(0, 0.5, 'stress')
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_158_0.png)

## 10.5 Nonlinear dimensionality reduction

Sources:

- Scikit-learn documentation
- Wikipedia

Nonlinear dimensionality reduction or **manifold learning** covers unsupervised methods that attempt to identify low-dimensional manifolds within the original $P$-dimensional space that represent high data density. Then those methods provide a mapping from the high-dimensional space to the low-dimensional embedding.

### 10.5.1 Isomap

Isomap is a nonlinear dimensionality reduction method that combines a procedure to compute the distance matrix with MDS. The distance calculation is based on geodesic distances evaluated on neighborhood graph:

- 1. Determine the neighbors of each point. All points in some fixed radius or K nearest neighbors.
- 2. Construct a neighborhood graph. Each point is connected to other if it is a K nearest neighbor. Edge length equal to Euclidean distance.
- 3. Compute shortest path between pairs of points $d_{ij}$ to build the distance matrix D.
- 4. Apply MDS on D.

```
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
from sklearn import manifold, datasets

X, color = datasets.samples_generator.make_s_curve(1000, random_state=42)

fig = plt.figure(figsize=(10, 5))
plt.suptitle("Isomap Manifold Learning", fontsize=14)

ax = fig.add_subplot(121, projection='3d')
ax.scatter(X[:, 0], X[:, 1], X[:, 2], c=color, cmap=plt.cm.Spectral)
ax.view_init(4, -72)
plt.title('2D "S shape" manifold in 3D')

Y = manifold.Isomap(n_neighbors=10, n_components=2).fit_transform(X)
ax = fig.add_subplot(122)
plt.scatter(Y[:, 0], Y[:, 1], c=color, cmap=plt.cm.Spectral)
plt.title("Isomap")
plt.xlabel("First component")
plt.ylabel("Second component")
plt.axis('tight')
```

```
(-5.4164373180970316, 5.276311544714793, -1.2910940054965336, 1.23497771017066)
```

**Isomap Manifold Learning**

**2D "S shape" manifold in 3D**

![](img/c2ad4b400bf63af9804b2d44510f76a6_160_0.png)

**Isomap**

![](img/c2ad4b400bf63af9804b2d44510f76a6_160_1.png)

## 10.6 Exercises

### 10.6.1 PCA

**Write a basic PCA class**

Write a class BasicPCA with two methods:

- fit(X) that estimates the data mean, principal components directions V and the explained variance of each component.
- transform(X) that projects the data onto the principal components.

Check that your BasicPCA gave similar results, compared to the results from sklearn.

**Apply your Basic PCA on the iris dataset**

The data set is available at: https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/iris.csv

- Describe the data set. Should the dataset be standardized?
- Describe the structure of correlations among variables.
- Compute a PCA with the maximum number of components.
- Compute the cumulative explained variance ratio. Determine the number of components K by your computed values.
- Print the $K$ principal components directions and correlations of the $K$ principal components with the original variables. Interpret the contribution of the original variables into the PC.
- Plot the samples projected into the $K$ first PCs.
- Color samples by their species.

### 10.6.2 MDS

Apply MDS from sklearn on the iris dataset available at: https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/iris.csv

- Center and scale the dataset.
- Compute Euclidean pairwise distances matrix.
- Select the number of components.
- Show that classical MDS on Euclidean pairwise distances matrix is equivalent to PCA.

## CLUSTERING

Wikipedia: Cluster analysis or clustering is the task of grouping a set of objects in such a way that objects in the same group (called a cluster) are more similar (in some sense or another) to each other than to those in other groups (clusters). Clustering is one of the main tasks of exploratory data mining, and a common technique for statistical data analysis, used in many fields, including machine learning, pattern recognition, image analysis, information retrieval, and bioinformatics.

Sources: http://scikit-learn.org/stable/modules/clustering.html

### 11.1 K-means clustering

Source: C. M. Bishop *Pattern Recognition and Machine Learning*, Springer, 2006

Suppose we have a data set $X = \{x_1, \cdots , x_N\}$ that consists of $N$ observations of a random $D$-dimensional Euclidean variable $x$. Our goal is to partition the data set into some number, $K$, of clusters, where we shall suppose for the moment that the value of $K$ is given. Intuitively, we might think of a cluster as comprising a group of data points whose inter-point distances are small compared to the distances to points outside of the cluster. We can formalize this notion by first introducing a set of $D$-dimensional vectors $\mu_k$, where $k = 1, \ldots , K$, in which $\mu_k$ is a **prototype** associated with the $k^{th}$ cluster. As we shall see shortly, we can think of the $\mu_k$ as representing the centres of the clusters. Our goal is then to find an assignment of data points to clusters, as well as a set of vectors $\{\mu_k\}$, such that the sum of the squares of the distances of each data point to its closest prototype vector $\mu_k$, is at a minimum.

It is convenient at this point to define some notation to describe the assignment of data points to clusters. For each data point $x_i$, we introduce a corresponding set of binary indicator variables $r_{ik} \in \{0,1\}$, where $k = 1, \ldots , K$, that describes which of the $K$ clusters the data point $x_i$ is assigned to, so that if data point $x_i$ is assigned to cluster $k$ then $r_{ik} = 1$, and $r_{ij} = 0$ for $j \neq k$. This is known as the 1-of-$K$ coding scheme. We can then define an objective function, denoted **inertia**, as

$J(r, \mu) = \sum_{i}^{N} \sum_{k}^{K} r_{ik} \|x_i - \mu_k\|_2^2$

which represents the sum of the squares of the Euclidean distances of each data point to its assigned vector $\mu_k$. Our goal is to find values for the $\{r_{ik}\}$ and the $\{\mu_k\}$ so as to minimize the function $J$. We can do this through an iterative procedure in which each iteration involves two successive steps corresponding to successive optimizations with respect to the $r_{ik}$ and the $\mu_k$. First we choose some initial values for the $\mu_k$. Then in the first phase we minimize $J$ with respect to the $r_{ik}$, keeping the $\mu_k$ fixed. In the second phase we minimize $J$ with respect to
