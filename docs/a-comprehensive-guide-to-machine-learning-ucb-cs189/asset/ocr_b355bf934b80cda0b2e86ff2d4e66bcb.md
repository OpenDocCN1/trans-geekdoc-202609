# # Chapter 2

# # Probabilistic Models in Machine Learning

# ## 2.1 MLE and MAP

So far, we've explored two approaches of the least squares framework, Ordinary Least Squares and Ridge Regression:

```
$w_{OLS}^* = \arg \min_{\mathbf{w}} ||\mathbf{y} - \mathbf{X}\mathbf{w}||_2^2 = \arg \min_{\mathbf{w}} \sum_{i=1}^n (y_i - \mathbf{x}_i^T\mathbf{w})^2$
```

```
$w_{RIDGE}^* = \arg \min_{\mathbf{w}} ||\mathbf{y} - \mathbf{X}\mathbf{w}||_2^2 + \lambda|\mathbf{w}||_2^2 = \arg \min_{\mathbf{w}} \sum_{i=1}^n (y_i - \mathbf{x}_i^T\mathbf{w})^2 + \lambda \sum_{j=1}^d w_j^2$
```

One question that you may have been asking yourself is why we are using the squared error to measure the effectiveness of our model, and why we use the $l^2$ norm for the model weights (and not other norm). We will justify all of these design choices by exploring the statistical interpretations of supervised learning methods and in particular, regression methods. In more concrete terms, we will use a variety of concepts from probability, such as Gaussians, MLE and MAP, to validate what we done so far through a different lens.

# ## Optimization in Model Space

Let's look at a simple regression model:

```
$f(x) = slope \cdot x + intercept$
```

Our goal is to find the optimal slope and intercept values that we believe describe the data. Each arbitrary (slope, intercept) pairs a line in data space. However, it can be viewed as a single point in model space. Learning the optimal model amounts to fitting a line to the data points in the data space; it's equivalent to locating the optimal parameter point in the model space: