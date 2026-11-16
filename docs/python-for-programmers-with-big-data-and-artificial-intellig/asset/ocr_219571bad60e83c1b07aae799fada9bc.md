# Creating a TSNE Estimator for Dimensionality Reduction

Next, we’ll use the TSNE estimator (from the sklearn.manifold module) to perform dimensionality reduction. This estimator uses an algorithm called t-distributed Stochastic Neighbor Embedding (t-SNE) ⁰ to analyze a dataset’s features and reduce them to the specified number of dimensions. We first tried the popular PCA (principal components analysis) estimator but did not like the results we were getting, so we switched to TSNE. We’ll show PCA later in this case study.

⁰The algorithms details are beyond this books scope. For more information, see tps://scikit-learn.org/stable/modules/manifold.html#t-sne.

Let’s create a TSNE object for reducing a dataset’s features to two dimensions, as specified by the keyword argument n_components. As with the other estimators we’ve presented, we used the random_state keyword argument to ensure the reproducibility of the “render sequence” when we display the digit clusters:

lick here to view code image

```
In [3]: from sklearn.manifold import TSNE

In [4]: tsne = TSNE(n_components=2, random_state=11)
```

# Transforming the Digits Dataset's Features into Two Dimensions

Dimensionality reduction in scikit-learn typically involves two steps—training the estimator with the dataset, then using the estimator to transform the data into the specified number of dimensions. These steps can be performed separately with the TSNE methods fit and transform, or they can be performed in one statement using the fit_transform method: ¹

¹Every call to fit_transform trains the estimator. If you intend to reuse the estimator to reduce the dimensions of samples multiple times, use fit to once train the estimator, then use transform to perform the reductions. We’ll use this technique with PCA later in this case study.

lick here to view code image

```
In [5]: reduced_data = tsne.fit_transform(digits.data)
```