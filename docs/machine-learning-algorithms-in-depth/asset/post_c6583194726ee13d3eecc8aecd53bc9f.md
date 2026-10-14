
```
if __name__ == "__main__":

#load data
iris = load_iris()
X = iris.data[:, [2,3]]
y = iris.target

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2,
    random_state=42)

print("decision tree classifier...")
tree_clf = DecisionTreeClassifier(max_depth = 3)
tree_clf.fit(X_train, y_train)

print("prediction...")
y_pred = tree_clf.predict(X_test)

tree_clf_acc = accuracy_score(y_test, y_pred)
print("test set accuracy: ", tree_clf_acc)
```

As we can see from the output, we achieve the test classification accuracy of 80% on the iris dataset.

## 5.7 Exercises

- 5.1 Given a data point y ∈ R^d and a hyperplane θ·x+θ₀=0, compute the Euclidean distance from the point to the hyperplane.
- 5.2 Given a primal linear program (LP) min cᵀ x subject to Ax <= b, x >= 0, write down the dual version of the LP.
- 5.3 Show that the radial basis function (RBF) kernel is equivalent to computing similarity between two infinite dimensional feature vectors.
- 5.4 Verify that the learning rate schedule ηₖ = (τ₀ + k)⁻ᵏ satisfies Robbins-Monro conditions.
- 5.5 Compute the derivative of the sigmoid function σ(a) = [1 + exp(−a)]⁻¹.
- 5.6 Compute the runtime and memory complexity of the Bernoulli naive Bayes algorithm.

## Summary

- The goal of a classification algorithm is to learn a mapping from inputs x to outputs y, where y is a discrete quantity.
- Perceptron is a classification algorithm that updates the decision boundary until there are no more classification mistakes.
- SVM is a max-margin classifier. The training data points that lie on the margin boundaries become support vectors.
- Logistic regression is a classification algorithm that computes class conditional density based on a softmax function.
- The naive Bayes algorithm assumes features are conditionally independent, given the class label. It is commonly used in document classification.
- The CART decision tree is a greedy, recursive algorithm that finds the optimum feature splits by minimizing an objective function, such as the Gini index.

## Regression algorithms

![](img/325742126d3ff007c6c385f4ffb5c3be_126_0.png)

**This chapter covers**
- Introducing regression
- Bayesian linear regression
- Hierarchical Bayesian regression
- KNN regression
- Gaussian process regression

In the previous chapter, we looked at supervised algorithms for classification. In this chapter, we will focus on supervised learning, in which we are trying to predict a continuous quantity. We will study four intriguing regression algorithms, which we will derive from the first principles: Bayesian linear regression, hierarchical Bayesian regression, KNN regression, and Gaussian process regression. These algorithms were selected because they span several important applications and illustrate diverse mathematical concepts. Regression algorithms are useful in a variety of applications. For example, they can be used to predict the price of financial assets or predict CO₂ levels in the atmosphere. Let’s begin by reviewing the fundamentals of regression.

### 6.1 Introduction to regression

In supervised learning, we are given a dataset D = {(x₁, y₁), ..., (xₘ, yₘ)} consisting of tuples of data x and labels y. The goal of a regression algorithm is to learn a mapping from inputs x to outputs y, where y is a continuous quantity (i.e., y ∈ R).

A regressor f can be viewed as a mapping between a d-dimensional feature vector φ(x) and a label y (i.e., f: Rᵈ → R). Regression problems are typically harder (to achieve higher accuracy) compared to classification problems because we are trying to predict a continuous quantity. Moreover, we are often interested in predicting future response variable y based on past training data.

One of the most widely used models for regression is linear regression, which models the response variable y as a linear combination of input feature vectors φ(x).

y(x) = wᵀ φ(x) + ε = Σ_{d=1}^D w_d φ(x_d) + ε  (6.1)
Features ↑ φ(x) ↓ Gaussian noise
Regression weights ↓ wᵀ

Here, ε is the residual error between our linear predictions and the true response. We can characterize the quality of our regressor based on the mean squared error (MSE).

MSE(w) = E[(y - f(x;w))²] = 1/N Σ_{i=1}^N (y_i - wᵀ φ(x_i))²  (6.2)
Prediction ↑ f(x;w)
Ground truth ↓ y

In this chapter, we will look at several important regression models, starting with Bayesian and KNN regression, and their extensions to hierarchical regression models, and concluding with Gaussian process (GP) regression. We'll focus on both the theory and implementation of each model from scratch.

### 6.2 Bayesian linear regression

Recall that we can write the linear regression as y(x) = wᵀ x + ε. If we assume that ε ~ N(0, σ²) is a zero-mean Gaussian RV with a variance σ², then we can formulate linear regression as follows.

p(y|x, θ) = N(y|wᵀ x, σ²)  (6.3)

Here, w are regression coefficients. To fit a linear regression model to data, we minimize the negative log likelihood.

$$\begin{aligned}\text{NLL}(w, \sigma^2) &= -\log p(y|x, \theta) \\
&= -\log \prod_{n=1}^N \left[ \frac{1}{\sqrt{2\pi\sigma^2}} \exp\left[-\frac{1}{2\sigma^2} (y_n - w^T x)^2\right] \right] \\
&= -\sum_{n=1}^N \log\left(\frac{1}{\sqrt{2\pi\sigma^2}}\right) + \sum_{n=1}^N \frac{1}{2\sigma^2} (y_n - w^T x)^2 \\
&= \frac{1}{2\sigma^2} \sum_{n=1}^N (y_n - w^T x)^2 + \frac{N}{2} \log(2\pi\sigma^2) \tag{6.4}\end{aligned}$$

Keeping $\sigma^2$ fixed and differentiating with respect to $w$, we get the following equation.

$$2X^T X w - 2X^T y + 2\lambda w = 0 \tag{6.5}$$

From equation 6.5, we can write the following.

$$\hat{w} = (X^T X + \lambda I)^{-1} X^T y \tag{6.6}$$

One problem with the estimation in equation 6.6 is that it can result in overfitting. To make the Bayesian linear regression robust against overfitting, we can encourage the parameters to be small by placing a zero-mean Gaussian prior.

$$p(w) = \prod_{d} N(w_d|0, \tau^2) \tag{6.7}$$

Thus, we can rewrite our regularized objective as follows.

$$\min_{w,\sigma^2} \text{NLL}(w, \sigma^2) + \lambda \|w\|_2^2 \tag{6.8}$$

Solving for $w$ as before, we get the following coefficients.

$$\hat{w}_{ridge} = (X^T X + \lambda I)^{-1} X^T y \tag{6.9}$$

We can learn the parameters $w$ using gradient descent! Let’s look at the pseudo-code in figure 6.1.

```
1: class ridge_reg:
2: function fit(X, y)
3: for i = 1, 2, ..., num_iter
4:   ŷ = w^T X
5:   grad = - (y - ŷ)^T X + λ w
6:   w = w - η_i grad ← Update regression weights
7: end for
8: return w
9: function predict(w, X)
10: ŷ = w^T X ← Make a prediction
11: return ŷ
```

Figure 6.1 Bayesian linear regression pseudo-code

The ridge_reg class consists of the fit and predict functions. In the fit function, we compute the gradient of the objective function wrt w and update the weight parameters. In the predict function, we use the learned regression weights to make a prediction on test data.

### Listing 6.1 Bayesian linear regression

```
import math
import numpy as np
import pandas as pd

import matplotlib.pyplot as plt
from sklearn.datasets import fetch_california_housing

class ridge_reg():
    def __init__(self, n_iter=20, learning_rate=1e-3, lmbda=0.1):
        self.n_iter = n_iter
        self.learning_rate = learning_rate
        self.lmbda = lmbda

    def fit(self, X, y):
        X = np.insert(X, 0, 1, axis=1)
        self.loss = []
        self.w = np.random.rand(X.shape[1])
        for i in range(self.n_iter):
            y_pred = X.dot(self.w)
            mse = np.mean(0.5*(y - y_pred)**2 + 0.5*self.lmbda*self.w.T.dot(self.w))
            self.loss.append(mse)
            print(" %d iter, mse: %.4f" % (i, mse))
            grad_w = - (y - y_pred).dot(X) + self.lmbda*self.w
            self.w -= self.learning_rate * grad_w

    def predict(self, X):
        X = np.insert(X, 0, 1, axis=1)
        y_pred = X.dot(self.w)
        return y_pred

if __name__ == "__main__":

    X, y = fetch_california_housing(return_X_y=True)
    X_reg = X[:,2].reshape(-1,1)
    X_std = (X_reg - X_reg.mean())/X.std()
    y_std = (y - y.mean())/y.std()

    X_std = X_std[:200,:]
    y_std = y_std[:200]

    rr = ridge_reg()
    rr.fit(X_std, y_std)
    y_pred = rr.predict(X_std)

    print(rr.w)

    plt.figure()
    plt.plot(rr.loss)
    plt.xlabel('Epoch')
    plt.ylabel('Loss')
    plt.tight_layout()
    plt.show()

    plt.figure()
    plt.scatter(X_std, y_std)
    plt.plot(np.linspace(-1,1), rr.w[1]*np.linspace(-1,1)+rr.w[0], c='red')
    plt.xlim([-0.01,0.01])
    plt.xlabel("scaled average num of rooms")
    plt.ylabel("scaled house price")
    plt.show()
```

Inserts const 1 for the bias term

Computes the gradient of NLL(w) wrt w

Updates the weights

Inserts const 1 for the bias term

Average number of rooms

Standard scaling

Figure 6.2 shows the output of Bayesian linear regression algorithm.

![](img/325742126d3ff007c6c385f4ffb5c3be_130_0.png)

**Figure 6.2** Bayesian linear regression loss function (left) and plot (right)
