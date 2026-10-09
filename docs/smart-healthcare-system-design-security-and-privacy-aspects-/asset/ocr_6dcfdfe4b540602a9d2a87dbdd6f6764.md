![](bbox=[0.11, 0.1, 0.89, 0.33])

**Figure 3.2** Kernel Function on non-linear SVM.

W is a weight vector (w₁, w₂, ...wₙ), n is the number of attributes and b is a scalar. As the X vector which lies very close to it the maximum margin hyperplane is described.

Non-linear mapping requires the kernel trick, which is a two-vector dot product. The kernel is associated to the transformation Φ(Xi) with the equation K(xi,xj) = Φ(xi) · Φ(xj). A sample non-linear transformation on 6D space for a given 3D vector X = {x1,x2,x3} using the Kernel mapping can be given as Φ1(X) = x1, Φ2(X) = x2, Φ3(x3) = x3, Φ4(X) = (x1)², Φ5(X) = (x1x2), Φ6(X) = (x1x3). Further this can be processed like a linear data with the decision boundary. Further the kernel functions are Polynomial, Gaussian, sigmoid etc.

# 3.1.2.3 Gradient Boosting

Gradient Boosting is a classification problem that builds a learner and predicts the test sample based on ensemble of weak prediction models. The algorithm is an additive model that performs optimization with differentiable loss functions. Basically decision trees are used for it and then generalize through optimization based on cost function. Thereby becomes a strong predictive model.

As this improves the strength of other learning algorithms, the idea is known as Probability Approximately Correct (PAC) learning. The hypothesis boosting tests identify the weak learner that was poorly classified and examples that were successfully classified to build a perfect model. As a whole gradient boosting involves three features, they are