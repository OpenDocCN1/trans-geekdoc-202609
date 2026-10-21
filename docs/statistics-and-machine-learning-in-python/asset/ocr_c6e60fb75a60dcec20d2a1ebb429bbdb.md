# Isomap Manifold Learning

# 2D "S shape" manifold in 3D

![](bbox=[0.17, 0.17, 0.45, 0.34])

# Isomap

![](bbox=[0.53, 0.12, 0.88, 0.4])

# 10.6 Exercises

# 10.6.1 PCA

# Write a basic PCA class

Write a class BasicPCA with two methods:

+   - fit(X) that estimates the data mean, principal components directions V and the explained variance of each component.
+   - transform(X) that projects the data onto the principal components.

Check that your BasicPCA gave similar results, compared to the results from sklearn.

# Apply your Basic PCA on the iris dataset

The data set is available at: https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/iris.csv

+   - Describe the data set. Should the dataset been standardized?
+   - Describe the structure of correlations among variables.
+   - Compute a PCA with the maximum number of components.
+   - Compute the cumulative explained variance ratio. Determine the number of components K by your computed values.