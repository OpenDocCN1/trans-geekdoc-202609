+   - Print the $K$ principal components directions and correlations of the $K$ principal components with the original variables. Interpret the contribution of the original variables into the PC.
+   - Plot the samples projected into the $K$ first PCs.
+   - Color samples by their species.

# 10.6.2 MDS

Apply MDS from sklearn on the iris dataset available at: https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/iris.csv

+   - Center and scale the dataset.
+   - Compute Euclidean pairwise distances matrix.
+   - Select the number of components.
+   - Show that classical MDS on Euclidean pairwise distances matrix is equivalent to PCA.