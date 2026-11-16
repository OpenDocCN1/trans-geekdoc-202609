# 7.2 NON-LINEAR SVM

The Non-linear Support Vector Machine (SVM) is an extension of the linear SVM that enables the classification of data that is not linearly separable in its original feature space. By applying the kernel trick, non-linear SVMs can transform the data into a higher-dimensional space, where it might become linearly separable, thus allowing the SVM to find more complex decision boundaries. This technique plays a crucial role in tackling intricate classification tasks across various domains.

**Kernel Trick and Feature Mapping:** The kernel trick is the essence of non-linear SVM. It avoids explicitly transforming data into a higher-dimensional space but calculates the dot product between data points in that space. This is achieved through a kernel function, which defines the similarity or distance between data points in the transformed space without explicitly computing the transformation itself.

**Kernel Functions:** Various kernel functions are used in non-linear SVMs to define the similarity between data points. Common kernel functions include polynomial kernels, radial basis function (RBF) kernels, sigmoid kernels, and more. Each

[144]

kernel has its strengths and is suitable for different types of data and decision boundaries.

**Mapping to Higher Dimensions:** The kernel trick allows non-linear SVM to effectively operate in a higher-dimensional feature space without the need to explicitly calculate the coordinates in that space. This is critical in maintaining computational efficiency even when the transformed space is high-dimensional.

**Radial Basis Function (RBF) Kernel:** The RBF kernel is one of the most popular kernel functions. It maps data points to an infinite-dimensional space, providing a flexible means to capture intricate decision boundaries. RBF kernels are well-suited for scenarios where the relationship between features and the target is highly complex.

**Decision Boundaries in Transformed Space:** In the transformed space, the decision boundary may appear linear, even if the original feature space's boundary was non-linear. This is because the kernel trick enables the SVM to capture intricate relationships between data points through the dot product.

[145]