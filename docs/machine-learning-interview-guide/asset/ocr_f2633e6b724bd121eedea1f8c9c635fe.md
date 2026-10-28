original variables, and this results in the decreased interpretability of clusters.

+   - Linear assumption: Another weakness of PCA is that it presupposes linear relationships between the variables and, therefore, may not be very useful when the actual relationships are non-linear—which often is the case.
+   - Preservation of variance: On the other hand, PCA preserves most of the variance and does not cluster all the features that are potentially essential for clustering as they have low variance.
+   - Sensitivity to outliers: When it comes to the sensitivity to outliers, PCA can be fragile in the presence of outliers, which may affect both the estimation of PCs, and, therefore, the clustering.
+   - Handling of categorical data: In PCA, there are certain limitations as the technique is primarily for numerical data and cannot accommodate categorical variables directly, which may require certain transformation procedures that could possibly result in loss of information or misrepresentation of data.

Knowing these limitations can help you in the right application of PCA in clustering tasks and in thinking about the other methods if applicable.

# Question 12: Can you explain the relationship between PCA and variance explained?

# Answer: A concise explanation of the relationship between PCA and variance explained is as follows:

+   - Variance captured by PCs: Every single accessing component of PCA holds a certain extent of variance in the original data collection. The first PC accounts for the largest amount of variance, with the 2nd, 3rd, ...,