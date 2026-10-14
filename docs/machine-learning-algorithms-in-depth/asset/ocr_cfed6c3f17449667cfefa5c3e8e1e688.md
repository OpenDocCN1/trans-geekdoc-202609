we have several possible gradients at that point, which are collectively known as subdifferential. Since hinge loss is a piecewise linear function, the gradient for z_i > 1 is equal to 0, while the gradient for z_i ≤ 1 is equal to equation 5.5.

∇_θ(1 - y_i(θ·x_i + θ0)) = -y_i x_i
∇_{θ0}(1 - y_i(θ·x_i + θ0)) = -y_i  (5.5)

Combining the expressions in equation 5.5 with a stochastic gradient descent update (where eta is the learning rate), we have equation 5.6.

θ^{(k+1)} = θ^{(k)} - η_k ∇_θ Loss_h(y_i(θ·x_i + θ0))  (5.6)

We get the perceptron algorithm! In the next section, we'll talk about another important classification algorithm: support vector machine (SVM).

# 5.3 Support vector machine

In the previous section, we evaluated the performance of our classifier by minimizing the expected loss function (aka empirical risk). One problem with the current formulation is there are multiple classifiers (multiple parameter values θ and θ0) that can achieve the same empirical risk. So how do we choose the best model, and what does best mean?

One solution is to regularize the loss function to favor small parameter values, as shown in equation 5.7.

L_n(θ, θ0) = λ/2 ||θ||^2 + 1/n Σ_{i=1}^n Loss(y_i(θ·x_i + θ0))  (5.7)

Here, the regularization applies to θ but not θ0. The reason is because θ specifies the orientation of the decision boundary, whereas θ0 is related to its offset from the origin, which is unknown at the start.

Let's try to understand the decision boundary better from a geometric point of view. It's desirable for the decision boundary, first, to classify all data points correctly and, second, to be maximally removed from all the training examples (i.e., to have the maximum margin). Suppose condition 1 is met and to optimize for condition 2, we need to compute and maximize the distance from every training example to the decision boundary. Geometrically, this distance is as follows.

γ_i = y_i(θ·x_i + θ0) / ||θ||  (5.8)

Since we want to maximize the margin, we would like to maximize the minimum distance to the decision boundary across all data points (i.e., find max[min_i γ_i]). This