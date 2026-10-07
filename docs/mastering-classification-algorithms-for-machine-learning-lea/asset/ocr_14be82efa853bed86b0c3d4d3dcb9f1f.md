# MSE = $\frac{1}{m} \sum_{i=1}^m (\overline{y}_i - y_i)^2$

Here, m is the number of data points in the dataset.

In the example in Figure 4.7, m = 7. For clarity, we represent yhat (as used in Figure 4.7) as $\hat{y}$.

This formula for MSE is also called the **Cost Function** and is written as follows.

```
$J = \frac{1}{m} \sum_{i=1}^m (\overline{y}_i - y_i)^2$
```

In the preceding equation, we replace $\hat{y}$ with $eta_0 + \beta_1x_1 + \beta_2x_2$ as follows.

```
$J = \frac{1}{m} \sum_{i=1}^m ((\beta_0 + \beta_1x_1 + \beta_2x_2) - y_i)^2$
```

In this equation, we can analyze and obtain the minimum value for J. To minimize the cost function, we use the **Gradient Descent** algorithm.

> Note: We may use other measures like Mean Average Error (MAE) as a Cost Function instead of MSE.

# Gradient Descent algorithm

We can write the cost as a function of $\gamma$ and .

```
$J = f(\beta_{\mu}, \beta_{\nu'}, \beta_{\zeta})$
```

Differential calculus states that a function $f(x)$ is minimized when the function's derivative, $df/dx$, is ZERO. J is a function of multiple variables, so we must take the partial derivatives.

To obtain the minimum value of J, we must try different values of $\beta_{\mu}$, $\beta_{\nu'}$, and $\beta_{\zeta}$. The different values of $\beta_{\mu}$, $\beta_{\nu'}$ and $\beta_{\zeta}$ that we will try are determined using the following strategy:

+   - We set a threshold below, if we get a good value for J, we will consider that we have found the minimum. This is because we may never get to the point when the derivative is ZERO as we perform floating point operations. To demonstrate, let us say that the threshold is 0.
- We set an initial value for $\beta_{\mu}$ and $\beta_{\nu'}$. Let us say we have each $\beta_{\mu}$, $\beta_{\nu'}$ and $\beta_{\zeta}$ to 2 as the initial value.
- We compute the value of J for this set of $\beta_{\mu}$, $\beta_{\nu'}$ and $\beta_{\zeta}$.