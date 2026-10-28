correlated original features, known as the PCs.

Here is a brief explanation:

+   - **Orthogonal transformation**: Really it transforms the data, so that initially correlated features has new variables and moreover PCs are orthogonal to each other.
+   - **Reduction of redundancy**: Thus, unlike other techniques, PCA reduces the dimensionality of the dataset thus easing the problem of multicollinearity. This means that these are linear relations that define how much of the total variation in the data is explained by the selected components and how much these components are dependent on each other.
+   - **Retained information**: However, with PCA, only the main features are retained while other additional dimensions are removed, making the results have the most important information from the original features. The propagation enables the first few PCs to retain most of the variance of the data, therefore, important pattern and structure.

Due to its ability to map the data onto a new coordinate space where the axes are mutually orthogonal, this method is useful in controlling for issues of multicollinearity. The transformed data is easily analyzed and more robust to multicollinearity.

# Question 11: What are the limitations of PCA in clustering?

Answer: The limitations of PCA in clustering are:

+   - **Loss of interpretability**: PCA reorganizes original features into new and different features, which are almost often the PCs. These features often pose some difficulties in their interpretation compared to the