kernel methods, it achieves its operation by implicitly projecting the input data into a feature space of higher-dimension than the original one without necessarily computing the feature space transformation. This is done by replacing the dot product between the vectors in the original input space with a kernel function, which measures the similarity in the higher-dimensional space. Some of the kernel functions that are used in modeling include the linear kernel, which directly shows that SVMs are capable of handling the non-linear decision boundaries enclosed in the given data even without working in the higher-dimension spaces.

# **Question 7: Discuss the impact of choosing different kernel functions (for example, linear, polynomial, radial basis function) on SVM performance.**

**Answer:** The impact of choosing different kernel functions on SVM performance is as follows:

+   - **Linear kernel:**
+     - **Advantages:** Basic, effective, performs quite well with the linearly separable data.
+     - **Limitations:** The major drawback when it comes to using this type of analysis is that it is only able to capture relatively simple, and only linear patterns and associations.
+   - **Polynomial kernel:**
+     - **Advantages:** Can present non-linear relationships with obtainable variability regarding the degree of non-linearity.
+     - **Impact:** This may mean that higher degrees are likely to overfit the model.
+   - **Radial basis function (RBF) kernel:**