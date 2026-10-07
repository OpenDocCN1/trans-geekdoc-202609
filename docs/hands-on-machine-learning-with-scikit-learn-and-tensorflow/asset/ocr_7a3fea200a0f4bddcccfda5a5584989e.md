tors, so, for example, the first principal component is equal to pca.components_.T[:,
0]).

# Explained Variance Ratio

Another very useful piece of information is the explained variance ratio of each principal component, available via the explained_variance_ratio_ variable. It indicates the proportion of the dataset's variance that lies along the axis of each principal component. For example, let's look at the explained variance of the first two components of the 3D dataset represented in Figure 8-2:

```
>>> pca.explained_variance_ratio_
array([0.84248607, 0.14631839])
```

This tells you that 84.2% of the dataset's variance lies along the first axis, and 14.6% lies along the second axis. This leaves less than 1.2% for the third axis, so it is reasonable to assume that it probably carries little information.

# Choosing the Number of Dimensions

Instead of arbitrarily choosing the number of dimensions to reduce to, it is generally preferable to choose the number of dimensions that add up to a sufficiently large portion of the variance (e.g., 95%). Unless, of course you are reducing dimensionality for data visualization—in that you will generally want to reduce the dimensionality down to 2 or 3.

The following code computes PCA without reducing dimensionality, computes the minimum number of dimensions required to preserve 95% of the training set's variance:

```
pca = PCA()
pca.fit(X_train)
cumsum = np.cumsum(pca.explained_variance_ratio_)
d = np.argmax(cumsum >= 0.95) + 1
```

You could then specify n_components=d and run PCA again. However, there is a much better option: instead of specifying the number of components you want to preserve, you can set n_components to be a float between 0.0 and 1.0, indicating the ratio of variance you wish to preserve:

```
pca = PCA(n_components=0.95)
X_reduced = pca.fit_transform(X_train)
```

Another option is to plot the explained variance as a function of the number of dimensions (simply plot cumsum Figure 8-8). There will usually an elbow in the curve, where the explained variance stops growing fast. You can think of this as the intrinsic dimensionality of the dataset.