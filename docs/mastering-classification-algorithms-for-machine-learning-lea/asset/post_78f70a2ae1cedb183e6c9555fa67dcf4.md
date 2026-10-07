
# MSE = $\frac{1}{m} \sum_{i=1}^m (\overline{y}_i - y_i)^2$

Here, m is the number of data points in the dataset.

In the example in Figure 4.7, m = 7. For clarity, we represent yhat (as used in Figure 4.7) as $\hat{y}$.

This formula for MSE is also called the **Cost Function** and is written as follows.

```
$J = \frac{1}{m} \sum_{i=1}^m (\overline{y}_i - y_i)^2$
```

In the preceding equation, we replace $\hat{y}$ with $\beta_0 + \beta_1x_1 + \beta_2x_2$ as follows.

```
$J = \frac{1}{m} \sum_{i=1}^m ((\beta_0 + \beta_1x_1 + \beta_2x_2) - y_i)^2$
```

In this equation, we can analyze and obtain the minimum value for J. To minimize the cost function, we use the **Gradient Descent** algorithm.

> Note: We may use other measures like Mean Absolute Error (MAE) as a Cost Function instead of MSE.

## Gradient Descent algorithm

We can write the cost as a function of $\beta$.

```
$J = f(\beta_{\mu}, \beta_{\nu}, \beta_{\zeta})$
```

Differential calculus states that a function $f(x)$ is minimized when the function's derivative, $df/dx$, is ZERO. J is a function of multiple variables, so we must take the partial derivatives.

To obtain the minimum value of J, we must try different values of $\beta_{\mu}$, $\beta_{\nu}$, and $\beta_{\zeta}$. The different values of $\beta_{\mu}$, $\beta_{\nu}$ and $\beta_{\zeta}$ that we will try are determined using the following strategy:

- We set a threshold below, if we get a good value for J, we will consider that we have found the minimum. This is because we may never get to the point when the derivative is ZERO as we perform floating point operations. To demonstrate, let us say that the threshold is 0.
- We set an initial value for $\beta_{\mu}$ and $\beta_{\nu}$. Let us say we have each $\beta_{\mu}$, $\beta_{\nu}$ and $\beta_{\zeta}$ to 2 as the initial value.
- We compute the value of J for this set of $\beta_{\mu}$, $\beta_{\nu}$ and $\beta_{\zeta}$.

## Logistic Regression

If the value of J <= threshold, we stop and consider the values of $\beta_{0'}, \beta_{1'}$ and $\beta_{2'}$ as the point where we have found the best estimates.

If J > threshold, we compute new values for $\beta_{0'}, \beta_{1'}$ and $\beta_{2'}$

```
$$\beta_{0'} = \beta_{0} - \alpha \frac{\delta J}{\delta \beta_{0}}$$ where $\frac{\delta J}{\delta \beta_{0}}$ is the partial derivative of J with respect to $\beta_{0}$, and $\alpha$ is a hyperparameter called the learning rate.
```

```
$$\beta_{1'} = \beta_{1} - \frac{\delta J}{\delta \beta_{1}}$ where $\frac{\delta J}{\delta \beta_{1}}$ is the partial derivative of J with respect to $\beta_{1}$
```

```
$$\beta_{2'} = \beta_{2} - \frac{\delta J}{\delta \beta_{2}}$$ where $\frac{\delta J}{\delta \beta_{2}}$ is the partial derivative of J with respect to $\beta_{2}$
```

We repeat steps 3, 4, and 5. Let us understand the preceding strategy with some numbers. Let us consider that we start with $\beta_{0'}, \beta_{1'}, \beta_{2}$ set as 2. We can compute J as follows. From Figure 4.6, we get J = 7967.58. As J > 0 (threshold), we need to calculate the new values of $\beta_{0'}, \beta_{1'}$ and try again. To compute the values of $\beta_{0'}, \beta_{1'}$ and $\beta_{2}$, we need the values for $\frac{\delta J}{\delta \beta_{0}}, \frac{\delta J}{\delta \beta_{1}}$ and $\frac{\delta J}{\delta \beta_{2}}$.

```
$$\frac{\delta J}{\delta \beta_{0}} = \frac{1}{m} \sum_{i=1}^m 2((\beta_0 + \beta_1x_1 + \beta_2x_2) - y_i)x_{i,0}$$
$$\frac{\delta J}{\delta \beta_{1}} = \frac{1}{m} \sum_{i=1}^m 2((\beta_0 + \beta_1x_1 + \beta_2x_2) - y_i)x_{i,1}$$
$$\frac{\delta J}{\delta \beta_{2}} = \frac{1}{m} \sum_{i=1}^m 2((\beta_0 + \beta_1x_1 + \beta_2x_2) - y_i)x_{i,2}$$
```

Similarly, we can compute $\frac{\delta J}{\delta J}$.

## Mastering Algorithms for Machine Learning

As these are many calculations, the following is a Python program to do all the math and provide the result:

```python
import pandas as pd

A = [4, 6, 3, 7, 2, 3, 4]
B = [2, 6, 9, 5, 12, 9, 7]
C = [4.45, 8.5, 9.5, 8.6, 12.2, 9.4, 8]

df = pd.DataFrame({'A':A, 'B':B, 'C':C})

b0 = 2
b1 = 2
b2 = 2
alpha = 0.001
threshold = 0

for c in range(1000):
    # Compute the Cost
    J = 0
    for i in range(len(df)):
        yhat = b0 + b1 * df.loc[i,'A'] + b2 * df.loc[i,'B']
        y = df.loc[i,'C']
        J += (yhat - y)**2

    J *= (1 / len(df))
    print("Iteration: %d, Cost - %f" % (c, J))
    print("b0 - %f, b1 - %f, b2 - %f" % (b0, b1, b2))
    if abs(J) < threshold:
        break

    # Partial Derivatives
    sumdiff = 0
    sumdiff_x1 = 0
    sumdiff_x2 = 0
    for i in range(len(df)):
        yhat = b0 + b1 * df.loc[i,'A'] + b2 * df.loc[i,'B']
        y = df.loc[i,'C']
        sumdiff += (yhat - y)
        sumdiff_x1 += (yhat - y) * df.loc[i,'A']
        sumdiff_x2 += (yhat - y) * df.loc[i,'B']

    del_j_b0 = (1 / len(df)) * 2 * sumdiff
    del_j_b1 = (1 / len(df)) * 2 * sumdiff_x1
    del_j_b2 = (1 / len(df)) * 2 * sumdiff_x2

    b0 = b0 - (alpha * del_j_b0)
    b1 = b1 - (alpha * del_j_b1)
    b2 = b2 - (alpha * del_j_b2)
```
