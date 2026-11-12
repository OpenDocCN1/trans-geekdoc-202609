# 6.3.2.1 Concept

The fundamental objective of LDA is to identify a linear feature combination [15] that maximises the separation between different classes in a dataset. In other words, LDA looks for new features that outperform the original collection of features in differentiating across classes in a dataset.

The model can only be trained with labelled data because LDA is a supervised learning technique. LDA makes the assumption that the dataset has a normal distribution and that each class has its own mean and covariance matrix.

The basic objective of LDA is to project the data onto a lower-dimensional subspace that maximises the separation between different classes. The eigenvectors of the within-class scatter matrix and between-class scatter matrix are calculated to do this.

The distance between the means of several classes is calculated using the interclass scatter matrix. The within-class scatter matrix is used to compute the variance for each class. The data is then applied to these matrices' eigenvectors in order to map it onto a lower-dimensional subspace.

# 6.3.2.2 Implementation

The following stages can be used to divide up LDA implementation:

+   1) Data Preparation: The preparation of the data is the first step in adopting LDA. The dataset must be split into training and testing sets in order to accomplish this, and the data must then be annotated with the proper classes.
+   2) Calculate the mean vectors: The average of all the data points inside a class is used to calculate the mean vector for that class.
+   3) Determine the within-class scatter matrix: Add the covariance matrices for each class to get the scatter matrix within each class.
+   4) Calculate the between-class scatter matrix: The outer products of the mean vectors representing the differences between each class are added to produce the interclass scatter matrix.
+   5) Calculate the eigenvectors and eigenvalues: The inverse of the within-class scatter matrix times the between-class scatter matrix is used to get the matrix's eigenvectors and eigenvalues.
+   6) Choose the top k eigenvectors: A new matrix is created using the top k eigenvectors with the highest eigenvalues.
+   7) Transform the data: After being transformed, the data is then projected into the newly created subspace created by the chosen eigenvectors.
+   8) Train the model: Using the altered data, a classifier is lastly developed to forecast the class labels of fresh data points.

# 6.3.2.3 Advantages

+   1) Reduces dimensionality: LDA is a good way to make a dataset's dimensions less. LDA can streamline the data and make it simpler to analyze by projecting it onto a lower-dimensional subspace.