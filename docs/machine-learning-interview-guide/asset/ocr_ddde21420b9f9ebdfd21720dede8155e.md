# Question 1: Can you explain the concept of a support vector in the context of SVR?

In SVR the term support vector is used to represent the data points that are closest to the regression hyperplane. These points are important in defining of the position and the orientation of the hyperplane. The SVR algorithm arrives at the construction of the hyperplane in a way that provides the maximum margin, which is the distance between the hyperplane and those support vectors. Support vectors can be thought of as the basis of the decision boundary of the SVR model and have a direct impact on the behavior of the algorithm by extracting the basic form of the data while at the same time, eliminating noise in the data.

# Question 2: What are the key hyperparameters in an SVR, and how do they impact the model's performance?

In an SVR, the key hyperparameters include:

+   - **Kernel**: Defines the kind of function that is to be used for creating a higher dimensionality of the input data. Some of the available kernel functions that can be used are linear, polynomial, and **Radial Basis Function (RBF) kernels**.
+   - **Regularization parameter (C)**: Ensures the optimal level of maximizing the margin and, at the same time, minimizing the error. By having a large C value, the model can have more complicated decision boundaries which means it is a case of overfitting, but if the C value is small, the model will have larger margins that can lead to underfitting the model.
+   - **Epsilon (ε)**: Defines the acceptable level that allows no penalty to be imposed on the errors. It defines the level of tolerance of errors or the tube within which