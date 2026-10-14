# 6.1 Introduction to regression

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

# 6.2 Bayesian linear regression

Recall that we can write the linear regression as y(x) = wᵀ x + ε. If we assume that ε ~ N(0, σ²) is a zero-mean Gaussian RV with a variance σ², then we can formulate linear regression as follows.

p(y|x, θ) = N(y|wᵀ x, σ²)  (6.3)

Here, w are regression coefficients. To fit a linear regression model to data, we minimize the negative log likelihood.