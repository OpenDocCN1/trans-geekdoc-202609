# Sigmoid function

![](bbox=[0.293, 0.103, 0.706, 0.287])

**Figure 4.2** Sigmoid function converts of the decision function $h$ into a probability.

where $\mathcal{M}$ is the set of all misclassified samples. The samples on the wrong side of the decision boundary are penalized proportionally to their distances from the decision boundary. The decision boundary can be found using the **perceptron learning algorithm:**

+   1. Pick a random training sample $\mathbf{x}_i$;
2. If $y_i = 1$ and $h(\mathbf{x}_i) < 0$, update the decision function: $\mathbf{w} = \mathbf{w} + \eta\mathbf{x}_i$;
3. If $y_i = 0$ and $h(\mathbf{x}_i) \geq 0$, update the decision function: $\mathbf{w} = \mathbf{w} - \eta\mathbf{x}_i$.
The algorithm iterates between these three steps until convergence. Parameter $\eta$ is the learning rate, which is usually set to 1. Even though this algorithm works in practice, the convergence is not always guaranteed. This drawback is overcome by the logistic regression model that we will describe next.

# 4.1.3 Logistic regression

For samples it might be difficult to decide the correct label because they lie close to the decision boundary. It is useful to predict not only the label but also the **confidence** in the prediction. Logistic regression converts the output of the decision function $h$ into a probability using a **sigmoid** function $\sigma$

$$\sigma(h) = \frac{1}{1 + e^{-h}}$$

The sigmoid function is depicted in Fig. 4.2. Note that positive values of the decision function result in probabilities between 0.5 and 1, while negative values result in probabilities between 0 and 0.5. If a data point $\mathbf{x}$ on the decision boundary $h(\mathbf{x}) = 0$, the resulting probability will be 0.5. The probability that a binary label $y$ is given by the feature vector $\mathbf{x}$ can therefore be expressed as a conditional probability and modeled by