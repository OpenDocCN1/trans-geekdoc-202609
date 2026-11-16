The default value for the n_clusters parameter is 8. Often, you'll rely on domain experts knowledgeable about the data to help choose an appropriate k value. However, with hyperparameter tuning, you can estimate the appropriate k, as we'll do later. In this case, we know there are three species, so we'll use n_clusters=3 to see how well KMeans does in labeling the Iris samples. Once again, we used the random_state keyword argument for reproducibility.

# Fitting the Model

Next, we'll train the estimator by calling the KMeans object's fit method. This step performs the k-means algorithm discussed earlier:

lick here to view code image

```
In [24]: kmeans.fit(iris.data)
Out[24]:
KMeans(algorithm='auto', copy_x=True, init='k-means++', max_iter=300,
    n_clusters=3, n_init=10, n_jobs=None, precompute_distances='auto',
    random_state=11, tol=0.0001, verbose=0)
```

As with the other estimator's, the fit method returns the estimator object and IPython displays its string representation. You can see the KMeans default arguments at:

```
https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.h
```

hen the training completes, the KMeans object contains:

+   • A labels_ array with values from 0 to n_clusters - 1 (in this example, 0–2), indicating the clusters to which the samples belong.

+   • A cluster_centers_ array in which each row represents a centroid.

# Comparing the Computer Cluster Labels to the Iris Dataset's Target Values

Because the Iris dataset is labeled, we can look at its target array values to get a sense of how well the k-means algorithm clustered the samples for the three Iris species. With unlabeled data, we'd need to depend on a domain expert to help evaluate whether the predicted classes make sense.