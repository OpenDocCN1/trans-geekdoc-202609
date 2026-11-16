# shape:

lick here to view code image

```
In [32]: iris_pca.shape
Out[32]: (150, 2)
```

Note that we separately called the PCA estimator's fit and transform methods, rather than fit_transform, which we used with the TSNE estimator. In this example, we're going to reuse the trained estimator (produced with fit) to perform a second transform to reduce the cluster centroids from four dimensions to two. This will enable us to plot the centroid locations on each cluster.

# Visualizing the Reduced Data

Now that we've reduced the original dataset to only two dimensions, let's use a scatter plot to display the data. In this case, we'll use Seaborn's scatterplot function. First, let's transform the reduced data into a DataFrame and add a species column that we'll use to determine the dot colors:

lick here to view code image

```
In [33]: iris_pca_df = pd.DataFrame(iris_pca,
    ...:
    ...:
    columns=['Component1', 'Component2'])

In [34]: iris_pca_df['species'] = iris_df.species
```

Next, let's scatterplot the data in Seaborn:

lick here to view code image

```
In [35]: axes = sns.scatterplot(data=iris_pca_df, x='Component1',
    ...:
    y='Component2', hue='species', legend='brief',
    ...:
    palette='cool')
    ...:
```

Each centroid in the KMeans object's cluster_centers_ array has the same number of features as the original dataset (four in this case). To plot the centroids, we must reduce their dimensions. You can think of a centroid as the “average” sample in its cluster. So each centroid should be transformed using the same PCA estimator we used