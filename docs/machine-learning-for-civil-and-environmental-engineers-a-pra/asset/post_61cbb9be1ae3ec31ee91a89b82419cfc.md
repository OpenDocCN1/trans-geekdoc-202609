

X = dataset
X.head(1)

```python
# Build a correlation Matrix
import seaborn as sns
plt.figure(figsize=(15, 13))
sns.heatmap(X.corr(),
            # annot = True,
            fmt = '.1g',
            center = 0,
            cmap = 'GnBu')
# linewidths = 1)
# linecolor = 'black')
plt.xticks(rotation=45, fontsize=18)
plt.yticks(rotation=45, fontsize=18)
(array([0.5, 1.5, 2.5, 3.5, 4.5, 5.5, 6.5, 7.5, 8.5, 9.5]),
<a list of 10 Text major ticklabel objects>)
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_316_0.png)

### Feature Scaling

```python
X = dataset.iloc[:, :9].values
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
X = sc.fit_transform(X)
```

#X=pd.DataFrame(data=X)
#X.to_excel('Xscaled.xlsx', index=False)
#Using the elbow method to find the optimal number of clusters

```python
from sklearn.cluster import KMeans
wcss = []
for i in range(1, 11):
    kmeans = KMeans(n_clusters = i, init = 'k-means++', random_state = 42)
    kmeans.fit(X)
    wcss.append(kmeans.inertia_)
plt.plot(range(1, 11), wcss)
plt.title(('The Elbow Method'),fontsize=20)
plt.xlabel(('Number of clusters'),fontsize=20)
plt.ylabel(('WCSS'),fontsize=20)
plt.xticks(fontsize = 14)
plt.yticks(fontsize = 14)
plt.show()
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_317_0.png)

## Training the K-Means model on the dataset

```python
from sklearn.cluster import KMeans
kmeans = KMeans(
    n_clusters=4, init="k-means++",
    n_init=10,
    tol=1e-04, random_state=42)
kmeans.fit(X)
y = kmeans.fit_predict(X)
mapping = {0:1, 1:2, 2:3, 3:4}
y = [mapping[i] for i in y]
```

## Describing features with a new figure

```python
import plotly.express as px
clusters=pd.DataFrame(X,columns=dataset.columns)
clusters['cluster']=y
polar=clusters.groupby("cluster").mean().reset_index()
polar=pd.melt(polar,id_vars=["cluster"])
#Fig4 = px.line_polar(polar, r="value", theta="variable", color="cluster",line_close=True,height=800,width=1000)
fig4 = px.line_polar(polar, r="value", theta="variable", color="cluster",line_close=True,height=600)
fig4.update_layout(
    polar = dict(
        radialaxis = tickfont_size = 21,
        angularaxis = dict(
            tickfont_size=26,
        ))
)
fig4.update_layout(legend_font_size=26)
fig4.show()
```

### Classification and regression trees (CART)

```python
X_normal = dataset.iloc[:, :9].values
from sklearn.tree import DecisionTreeClassifier
classifier = DecisionTreeClassifier(criterion = 'entropy', random_state = 0)
classifier.fit(X_normal, y)
DecisionTreeClassifier(criterion='entropy', random_state=0)
from sklearn import tree
fig, axes = plt.subplots(nrows = 1, ncols = 1, figsize = (8,8), dpi=200)
tree.plot_tree(classifier, feature_names = dataset.columns,filled = True, class_names=['1','2','3','4'],fontsize=9)
[Text(0.625, 0.9285714285714286, 'fc (MPa) <= 71.0\\nentropy = 1.913\\nsamples = 144\\nvalue = [32, 21, 56, 35]\\nclass = 3''),
Text(0.5, 0.7857142857142857, 'L (m) <= 4.3\\nentropy = 1.537\\nsamples = 113\\nvalue = [1, 21, 56, 35]\\nclass = 3''),
Text(0.375, 0.6428571428571429, 'C (mm) <= 36.5\\nentropy = 1.169\\nsamples = 82\\nvalue = [1, 21, 56, 4]\\nclass = 3''),
Text(0.25, 0.5, 'entropy = 0.0\\nsamples = 20\\nvalue = [0, 20, 0, 0]\\nclass = 2''),
Text(0.5, 0.5, 'K <= 0.85\\nentropy = 0.58\\nsamples = 62\\nvalue = [1, 1, 56, 4]\\nclass = 3'),
Text(0.25, 0.35714285714285715, 'r (%) <= 1.5\\nentropy = 0.137\\nsamples = 52\\nvalue = [1, 0, 51, 0]\\nclass = 3'),
Text(0.125, 0.21428571428571427, 'entropy = 0.0\\nsamples = 1\\nvalue = [1, 0, 0, 0]\\nclass = 1'),
Text(0.375, 0.21428571428571427, 'entropy = 0.0\\nsamples = 51\\nvalue = [0, 0, 51, 0]\\nclass = 3'),
Text(0.75, 0.35714285714285715, 'P (kN) <= 820.0\\nentropy = 1.361\\nsamples = 10\\nvalue = [0, 1, 5, 4]\\nclass = 3'),
Text(0.625, 0.21428571428571427, 'P (kN) <= 384.5\\nentropy = 0.722\\nsamples = 5\\nvalue = [0, 1, 0, 4]\\nclass = 4'),
Text(0.5, 0.07142857142857142, 'entropy = 0.0\\nsamples = 1\\nvalue = [0, 1, 0, 0]\\nclass = 2'),
Text(0.75, 0.07142857142857142, 'entropy = 0.0\\nsamples = 4\\nvalue = [0, 0, 0, 4]\\nclass = 4'),
Text(0.875, 0.21428571428571427, 'entropy = 0.0\\nsamples = 5\\nvalue = [0, 0, 5, 0]\\nclass = 3'),
Text(0.625, 0.42857142857142855, 'entropy = 0.0\\nsamples = 31\\nvalue = [0, 0, 0, 31]\\nclass = 4'),
Text(0.75, 0.7857142857142857, 'entropy = 0.0\\nsamples = 31\\nvalue = [31, 0, 0, 0]\\nclass = 1')]
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_319_0.png)

```python
text_representation = tree.export_text(classifier)
print(text_representation)
|--- feature_3 <= 71.00
|   |--- feature_2 <= 4.30
|   |   |--- feature_6 <= 36.50
|   |   |   |--- class: 4
|   |   |--- feature_6 > 36.50
|   |   |   |--- feature_5 <= 0.85
|   |   |   |   |--- feature_1 <= 1.50
|   |   |   |   |   |--- class: 2
|   |   |   |   |--- feature_1 > 1.50
|   |   |   |   |--- class: 3
|   |   |--- feature_5 > 0.85
|   |   |   |--- feature_8 <= 820.00
|   |   |   |   |--- feature_8 <= 384.50
|   |   |   |   |   |--- class: 4
|   |   |   |   |--- feature_8 > 384.50
|   |   |   |   |   |--- class: 1
| | | | | |--- feature_8 > 820.00
| | | | | |--- class: 3
| | | --- feature_2 > 4.30
| | | |--- class: 1
|--- feature_3 > 71.00
| |--- class: 2
```

### Visualizing clusters

```python
X = dataset.iloc[:, :9].values
y=np.array(y)
plt.scatter(X[y == 1, 3], X[y == 1, 8], s = 100, c = 'red', label = 'Cluster 1')
plt.scatter(X[y == 2, 3], X[y == 2, 8], s = 100, c = 'green', label = 'Cluster 2')
plt.scatter(X[y == 3, 3], X[y == 3, 8], s = 100, c = 'blue', label = 'Cluster 3')
plt.scatter(X[y == 4, 3], X[y == 4, 8], s = 100, c = 'cyan', label = 'Cluster 4')
plt.title('Clusters of RC columns')
plt.xlabel('fc')
plt.ylabel('P')
plt.legend()
plt.show()
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_320_0.png)

### FCM algorithm

```python
#%matplotlib inline
import pandas as pd
import numpy as np
from fcmeans import FCM
from matplotlib import pyplot as plt
```

```python
dataset = pd.read_excel('Fire-exposed RC columns.xlsx')
X = dataset.iloc[:, :9].values
```

```python
X = dataset.iloc[:, :9].values
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
X = sc.fit_transform(X)
```

```python
from sklearn.metrics import silhouette_samples, silhouette_score
import matplotlib.cm as cm
range_n_clusters = range( 2, 11 )
for n_clusters in range_n_clusters:

    fig, (ax1, ax2) = plt.subplots(1, 2)
    fig.set_size_inches(18, 7)

    ax1.set_xlim([-0.1, 1])
    ax1.set_ylim([0, len(X) + (n_clusters + 1) * 10])

    fcm = FCM(n_clusters=n_clusters)
    fcm.fit(X)
    y_fcm = fcm.predict(X)
    cluster_labels = y_fcm
    silhouette_avg = silhouette_score(X, cluster_labels)
    print("For n_clusters =", n_clusters,
          "The average silhouette_score is :", silhouette_avg)

    sample_silhouette_values = silhouette_samples(X, cluster_labels)

    y_lower = 10
    for i in range(n_clusters):
        ith_cluster_silhouette_values = \
            sample_silhouette_values[cluster_labels == i]

        ith_cluster_silhouette_values.sort()

        size_cluster_i = ith_cluster_silhouette_values.shape[0]
        y_upper = y_lower + size_cluster_i

        color = cm.nipy_spectral(float(i) / n_clusters)
        ax1.fill_betweenx(np.arange(y_lower, y_upper),
                          0, ith_cluster_silhouette_values,
                          facecolor=color, edgecolor=color, alpha=0.7)

        ax1.text(-0.05, y_lower + 0.5 * size_cluster_i, str(i))

        y_lower = y_upper + 10  # 10 for the 0 samples

    ax1.set_title("The silhouette plot for the various clusters.")
    ax1.set_xlabel("The silhouette coefficient values")
    ax1.set_ylabel("Cluster label")

    ax1.axvline(x=silhouette_avg, color="red", linestyle="--")

    ax1.set_yticks([])  # Clear the yaxis labels / ticks
    ax1.set_xticks([-0.1, 0, 0.2, 0.4, 0.6, 0.8, 1])

    colors = cm.nipy_spectral(cluster_labels.astype(float) / n_clusters)
    ax2.scatter(X[:, 0], X[:, 1], marker='.', s=30, lw=0, alpha=0.7,
                c=colors, edgecolor='k')
```

