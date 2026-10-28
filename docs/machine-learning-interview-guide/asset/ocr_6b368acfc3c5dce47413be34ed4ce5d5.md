Therefore, appropriate steps must be taken in the preprocessing and method used to deal with the data type to use in k-means for categorical attributes.

# **Question 12: What happens if the dataset contains missing values in K-means clustering?**

**Answer:** In case the dataset used in k-means clustering has some missing values then the results of the clustering exercises and the actual clusters formed are affected.

Here is what happens:

+   1. **Impact on distance calculation**: These missing values influence the way the distances are computed, specifically the similarities that are obtained in the course of comparing the data with centroids.
+   2. **Centroid calculation**: This serves to create a phenomenon of biased centroid positions or skewed positions, which are likely to affect the general clustering of the cluster.
+   3. **Incomplete cluster formation**: Many data points have missing values that can result in these values being omitted or attributed to the wrong cluster, preventing clean and clear clusters.
+   4. **Handling missing values**: Their action plans are imputation, elimination of records with missing data, and alteration of distance measures with missing data.

In general, it can be understood that missing values in k-means clustering should be thoroughly addressed and treated in a proper way so as not to affect the clustering process and to achieve proper k-means clusters.

# **Question 13: What are some variations/extensions of the traditional k-means algorithm?**