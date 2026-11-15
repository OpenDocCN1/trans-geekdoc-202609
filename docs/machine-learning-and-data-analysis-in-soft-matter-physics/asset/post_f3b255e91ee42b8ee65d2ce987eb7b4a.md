
```
```python
from sklearn.datasets import load_wine
winedata = load_wine()
X, y = winedata['data'], winedata['target']
print(X.shape)
print(y.shape)
```
```

```
```
(178, 13)
(178,)
```
```

Among the 13 features, we can pick any two and plot with matplotlib (we color-coded the different classes using the c argument):

```
```python
...
import matplotlib.pyplot as plt
plt.scatter(X[:,1], X[:,2], c=y)
plt.show()
```
```

![](img/c4a53cbbd40023d194b7887dddf3293b_125_0.png)

or we can also pick any three and show in 3D:

```
```python
...
ax = fig.add_subplot(projection='3d')
ax.scatter(X[:,1], X[:,2], X[:,3], c=y)
plt.show()
```
```

But this doesn't reveal much of how the data looks like, because majority of the features are not shown. We now resort to principal component analysis:

```
...
from sklearn.decomposition import PCA
pca = PCA()
Xt = pca.fit_transform(X)
plot = plt.scatter(Xt[:,0], Xt[:,1], c=y)
plt.legend(handles = plot.legend_elements()[0],
labels=list(winedata['target_names']))
plt.show()
```

![](img/c4a53cbbd40023d194b7887dddf3293b_126_1.png)

Here we transform the input data X by PCA into Xt. We consider only the first two columns, which contain the most information, and plot it in two dimensional. We can see that the purple class is quite distinctive, but there is still some overlap. If we scale the data before PCA, the result would be different:

```
...
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline
pca = PCA()
pipe = Pipeline([('scaler', StandardScaler()), ('pca', pca)])
Xt = pipe.fit_transform(X)
plot = plt.scatter(Xt[:,0], Xt[:,1], c=y)
plt.legend(handles = plot.legend_elements()[0],
labels=list(winedata['target_names']))
plt.show()
```

![](img/c4a53cbbd40023d194b7887dddf3293b_127_0.png)

Because PCA is sensitive to the scale, if we normalized each feature by StandardScaler we can see a better result. Here the different classes are more distinctive. By looking at this plot, we are confident that a simple model such as SVM can classify this dataset in high accuracy.

Putting these together, the following is the complete code to generate the visualizations:

```python
from sklearn.datasets import load_wine
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline
import matplotlib.pyplot as plt

# Load dataset
winedata = load_wine()
X, y = winedata['data'], winedata['target']
print("X shape:", X.shape)
print("y shape:", y.shape)

# Show any two features
plt.figure(figsize=(8,6))
plt.scatter(X[:,1], X[:,2], c=y)
plt.xlabel(winedata["feature_names"][1])
plt.ylabel(winedata["feature_names"][2])
plt.title("Two particular features of the wine dataset")
plt.show()

# Show any three features
fig = plt.figure(figsize=(10,8))
ax = fig.add_subplot(projection='3d')
ax.scatter(X[:,1], X[:,2], X[:,3], c=y)
ax.set_xlabel(winedata["feature_names"][1])
ax.set_ylabel(winedata["feature_names"][2])
ax.set_zlabel(winedata["feature_names"][3])
ax.set_title("Three particular features of the wine dataset")
plt.show()

# Show first two principal components without scaler
pca = PCA()
plt.figure(figsize=(8,6))
Xt = pca.fit_transform(X)
plot = plt.scatter(Xt[:,0], Xt[:,1], c=y)
plt.legend(handles=plot.legend_elements()[0], labels=list(winedata['target_names']))
plt.xlabel("PC1")
plt.ylabel("PC2")
plt.title("First two principal components")
plt.show()

# Show first two principal components with scaler
pca = PCA()
pipe = Pipeline([('scaler', StandardScaler()), ('pca', pca)])
plt.figure(figsize=(8,6))
Xt = pipe.fit_transform(X)
plot = plt.scatter(Xt[:,0], Xt[:,1], c=y)
plt.legend(handles=plot.legend_elements()[0], labels=list(winedata['target_names']))
plt.xlabel("PC1")
plt.ylabel("PC2")
plt.title("First two principal components after scaling")
plt.show()
```

If we apply the same method on a different dataset, such as MNIST handwritten digits, the scatterplot is not showing distinctive boundary and therefore it needs a more complicated model such as neural network to classify:

```python
from sklearn.datasets import load_digits
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline
import matplotlib.pyplot as plt

digitsdata = load_digits()
X, y = digitsdata['data'], digitsdata['target']
pca = PCA()
pipe = Pipeline([('scaler', StandardScaler()), ('pca', pca)])
plt.figure(figsize=(8,6))
Xt = pipe.fit_transform(X)
plot = plt.scatter(Xt[:,0], Xt[:,1], c=y)
plt.legend(handles=plot.legend_elements()[0], labels=list(digitsdata['target_names']))
plt.show()
```

![](img/c4a53cbbd40023d194b7887dddf3293b_130_0.png)

### 4.2.2 Visualizing the Explained Variance

PCA in essence is to rearrange the features by their linear combinations. Hence it is called a feature extraction technique. One characteristic of PCA is that the first principal component holds the most information about the dataset. The second principal component is more informative than the third, and so on.

To illustrate this idea, we can remove the principal components from the original dataset in steps and see how the dataset looks like. Let’s consider a dataset with fewer features, and show two features in a plot:

```python
from sklearn.datasets import load_iris
irisdata = load_iris()
X, y = irisdata['data'], irisdata['target']
plt.figure(figsize=(8,6))
plt.scatter(X[:,0], X[:,1], c=y)
plt.show()
```

![](img/c4a53cbbd40023d194b7887dddf3293b_130_1.png)

This is the iris dataset which has only four features. The features are in comparable scales and hence we can skip the scaler. With a 4-features data, the PCA can produce at most 4 principal components:

```python
...
pca = PCA().fit(X)
print(pca.components_)
```

| | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| 0 | 0.36138659 | -0.08452251 | 0.85667061 | 0.3582892 |
| 1 | 0.65658877 | 0.73016143 | -0.17337266 | -0.07548102 |
| 2 | -0.58202985 | 0.59791083 | 0.07623608 | 0.54583143 |
| 3 | -0.31548719 | 0.3197231 | 0.47983899 | -0.75365743 |

For example, the first row is the first principal axis on which the first principal component is created. For any data point p with features p =(a,b,c,d), since the principal axis is denoted by the vector v =(0.36,-0.08,0.86,0.36), the first principal component of this data point has the value 0.36×a–0.08×b+0.86×c+0.36×d on the principal axis. Using vector dot product, this value can be denoted by

p · v

Therefore, with the dataset X as a 150 × 4 matrix (150 data points, each has 4 features), we can map each data point into to the value on this principal axis by matrix-vector multiplication:

X · v

and the result is a vector of length 150. Now if we remove from each data point the corresponding value along the principal axis vector, that would be

X−(X · v) · vᵀ

where the transposed vector vᵀ is a row and X · v is a column. The product (X · v) · vᵀ follows matrix-matrix multiplication and the result is a 150×4 matrix, same dimension as X.

If we plot the first two feature of (X · v) · vᵀ, it looks like this:

```python
...
# Remove PC1
Xmean = X - X.mean(axis=0)
value = Xmean @ pca.components_[0]
pc1 = value.reshape(-1,1) @ pca.components_[0].reshape(1,-1)
Xremove = X - pc1
plt.scatter(Xremove[:,0], Xremove[:,1], c=y)
plt.show()
```

![](img/c4a53cbbd40023d194b7887dddf3293b_132_0.png)

The numpy array Xmean is to shift the features of X to centered at zero. This is required for PCA. Then the array value is computed by matrix-vector multiplication.

The array value is the magnitude of each data point mapped on the principal axis. So if we multiply this value to the principal axis vector we get back an array pc1. Removing this from the original dataset X, we get a new array Xremove. In the plot we observed that the points on the scatter plot crumbled together and the cluster of each class is less distinctive than before. This means we removed a lot of information by removing the first principal component. If we repeat the same process again, the points are further crumbled:

```python
... Remove PC2
value = Xmean @ pca.components_[1]
pc2 = value.reshape(-1,1) @ pca.components_[1].reshape(1,-1)
Xremove = Xremove - pc2
plt.scatter(Xremove[:,0], Xremove[:,1], c=y)
plt.show()
```

![](img/c4a53cbbd40023d194b7887dddf3293b_132_1.png)
