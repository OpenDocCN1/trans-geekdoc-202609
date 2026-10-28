+   4. **Random Partition initialization**: Select *K* distinct instances and randomly split the dataset into *K* equal groups, and the centroid of the group is the mean.
+   5. **K-means++ initialization**: Selection of better initial centroids in k-means++ for large database by adding centroids using a weighted sampling algorithm.

# Question 10: How does k-means deal with high-dimensional data?

**Answer**: K-means clustering can be used on data of high-dimensionality; however, it may face certain difficulties because of the curse of dimensionality.

Here is how k-means deals with high-dimensional data:

+   - **Euclidean distance**: K-means uses Euclidean distance as the distance metric by default, however, as the dimensionality of space increases, the distances between points may decrease, leading to inferior properties where distance measure is rather limited.
+   - **Dimension reduction**: It is always a good idea to perform dimensionality reduction on the dataset before clustering, in order to maintain important structures and remove noise; the methods **principal component analysis (PCA)** or **t-distributed Stochastic Neighbor Embedding (t-SNE)** can be used for this purpose.
+   - **Feature selection**: Feature selection is selecting a few features that can be more informative than the complete set, thus lessening the dimensionality.
+   - **Normalization**: The scaling or normalization is used to standardize the range of a dataset to improve clustering by making sure that all feature values contribute significantly to the distances.