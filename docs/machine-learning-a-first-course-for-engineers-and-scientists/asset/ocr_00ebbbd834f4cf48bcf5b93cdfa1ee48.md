# 7.4 Gradient boosting

> Time to reflect 7.4: We have described boosting algorithms as a greedy stepwise training of an additive model. Based on this interpretation, another approach for training these models is by coordinate ascent (see Section 5.4). That is, instead of adding a new component at each iteration of the training algorithm, stopping after B iterations, we can fix the number of components and cycle through them (updating one component at a time) until convergence. What are the possible drawbacks and benefits of this alternative training approach?

While presented for classification in Method 7.3, gradient boosting can also be used for regression with minor modifications. As mentioned above, gradient boosting requires that it is at least everywhere differentiable, so that it is possible to compute the gradient of the loss function. However, some implementations of gradient boosting require stronger conditions, such as second order differentiability. The logistic loss (see Section 5.2) in is in this respect a “safe choice” which is infinitely differentiable and strongly convex, while still enjoying good statistical properties. As a consequence, the logistic loss is one of the most commonly used loss functions in practice.

We conclude this chapter by applying AdaBoost as well as gradient boosting to the music classification problem from Example 2.1 in Figure 7.9.

![](bbox=[0.125, 0.385, 0.879, 0.565])

Figure 7.9: Two boosting algorithms applied to the music classification problem from Example 2.1.