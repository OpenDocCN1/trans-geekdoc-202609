
![Tip](images/tip.png)The advantage of the mini-batch is that it can process data that won't fit in the available memory of your computer by fetching examples in small chunks from disk. The algorithm processes each chunk, updates the clusters, and then loads the next chunk. The only possible bottleneck is the speed of data transfer. The process takes more time than the classical algorithm, but when it’s finished computing (and it may take a few passages on all your data), you’ll have a complete model that’s not much different from the model you could have obtained using the standard algorithm.

![Remember](images/remember.png)`sklearn.cluster.MiniBatchKMeans` has two fit methods:

*   `fit`: Works with data in memory and stops after it processes the information available based on the batch size that you set using the `batch_size` parameter.

*   `partial_fit`: Processes the data in memory, but then remains open to start again when presented with new data, so it's perfect for streaming data in blocks from disk or from a network such as the Internet.

`sklearn.cluster.KMeans` offers all the standard parameters discussed earlier: the number of clusters (`n_clusters`) and the initialization method (`init`). Moreover, it offers the possibility to precompute distances (`precompute_distances`). If the number of effective iterations is high, `sklearn.cluster.KMeans` calculates the distances repetitively, wasting time. If you have memory and need speed, just set `precompute_distances` to `TRUE`, which stores all the calculations in advance. You can also instruct the algorithm to work in parallel (setting `n_job` to `-1` or `-2` if you want to keep one processor free for other operations) when it has to create many solutions simultaneously (because of different random initializations). Precomputing distances and parallel computation make the Python implementation currently the fastest available.

### Experimenting with K-means reliability

The book's first experiment to demonstrate K-means nuances uses a new dataset, the Palmer Penguins dataset, whose data were collected and made available by Dr. Kristen Gorman and the Palmer Station, Antarctica LTER, a member of the Long Term Ecological Research Network (Horst AM, Hill AP, Gorman KB (2020)). Read about the Palmer Penguins dataset at [`https://allisonhorst.github.io/palmerpenguins/`](https://allisonhorst.github.io/palmerpenguins/).

![Tip](images/tip.png)The Palmer Penguins dataset is a recent dataset and, from an educational perspective, a good replacement for the older Iris dataset. The Iris dataset, introduced by statistician Ronald Fisher in one of his papers in 1936, is a popular example dataset about three species of iris flowers that had their petals and sepals (part of the flower, supporting the petals when in bloom) measured. Because of its popularity, the Iris dataset appears in many books and tutorials, even though its data wasn’t always suitable for many statistical and machine learning tasks.

The Palmer Penguins dataset records the gender, body mass, flipper length, and bill length and depth (called *culmen*) of three species of penguins (Adelie, Chinstrap, and Gentoo). See [`http://marinebio.net/marinescience/04benthon/AApenguins.htm`](http://marinebio.net/marinescience/04benthon/AApenguins.htm) for more information. These penguins live on islands in the Palmer Archipelago, in the Antarctic. The examples aren’t balanced among classes (there are fewer Chinstrap), but it is balanced among genders (the count is for the female and male).

The following example downloads the data from the book’s dataset repository. It then divides the data among features (excluding the gender, but keeping all the numeric measures) and labels. Using `LabelEncoder` from Scikit-learn the example converts the penguin species names into numbers and prints their encodings.

```
import numpy as np
import pandas as pd
from sklearn.preprocessing import LabelEncoder
link = "https://github.com/lmassaron/datasets/"
link += "releases/download/1.0/penguins.feather"
penguins = pd.read_feather(link)
features = penguins.iloc[:,1:5]
le = LabelEncoder()
labels = le.fit_transform(penguins.species)
target_names = dict(zip(range(3), le.classes_))
print(target_names)
```

The experiment uses both of the two available K-means versions in Scikit-learn: the standard algorithm and the mini-batch version. In the Scikit-learn package, you must define a feature for each learning algorithm in advance, specifying its parameters. Therefore, you define two features, `k_means` and `mb_k_means`, which require three clusters, a smart initialization procedure (called *k-means++*), and raising the number of maximum iterations to a high figure (don't worry, usually the algorithm is quite fast). Because body size and the various measurements are on different scales, you first prepare a pipeline that will standardize the features and remove all correlations from them using PCA. By doing so, you can be confident that the Euclidean distance measurement that K-means computes works well. Finally, you transform the data and fit the features, and after a short delay, the computations complete.

```
from sklearn.pipeline import Pipeline
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import MiniBatchKMeans, KMeans
pca = Pipeline([('scaling', StandardScaler()), ('pca', PCA())])
k_means = KMeans(n_clusters=3, init='k-means++', max_iter=999, n_init=10, random:state=101)
mb_k_means = MiniBatchKMeans(n_clusters=3, init='k-means++', max_iter=999, batch_size=30, n_init=10, random:state=101)
pca_features = pca.fit_transform(features)
print('Explained variance:')
print(pca.named_steps['pca'].explained_variance_)
k_means.fit(pca_features)
mb_k_means.fit(pca_features)
```

During execution, the code prints the amount of variance explained by the PCA dimensions: 2.75, 0.78, 0.37 and 0.11. The first dimension is dominant and the first two dimensions account for the majority of variance. Printing the outputs bi-dimensionally allow you to understand how the cluster analysis worked. The following code prints a nice plot on your screen of how points distribute on a map made of the first and second PCA dimension, as shown in [Figure 12-2](#c12.xhtml#c12-fig-0002).

```
import matplotlib.pyplot as plt
plt.scatter(pca_features[:,0], pca_features[:,1], s=2**7, c=labels, edgecolors='lightgrey', alpha=0.85, cmap='Spectral')
plt.xlabel('pca_0')
plt.ylabel('pca_1')
plt.grid()
km:centers = k_means.cluster_centers_mbkm:centers = mb_k_means.cluster_centers_
plt.scatter(km:centers[:,0], km:centers[:,1], s=2**6, marker='s', c='orange', edgecolors='black')
plt.scatter(mbkm:centers[:,0], mbkm:centers[:,1], s=2**8, marker='*', c='yellow', edgecolors='black')
for class_no in range(0,3):
    plt.annotate(target_names[class_no], (pca_features[labels==class_no, 0].mean(), pca_features[labels==class_no, 1].mean()), fontsize=20)
plt.show()
```

![FIGURE 12-2: Clusters of penguins plotted on a chart based on first PCA dimensions.](images/9781119724018-fg1202.png)

[FIGURE 12-2:](#c12.xhtml#rc12-fig-0002) Clusters of penguins plotted on a chart based on first PCA dimensions.

Notice that the plot also displays the centroids — those from the standard algorithm as squares; those from the mini-batch version as stars — and they don’t differ all that much. This fact demonstrates how the different learning procedures lead to almost identical conclusions. Sometimes it’s amazing to see how even algorithms that are different may arrive at the same conclusions. When that doesn’t happen, you might have too much variance in the estimates, and each algorithm could have a very different learning strategy; yet, you’ll notice that machine learning algorithms often tend to get the same strong signals (though in the end they make different use of them).
