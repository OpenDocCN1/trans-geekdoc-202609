+   - n is the number of features
- x, is the i^{th} feature value.
- $	heta_j$ is the $j^{th}$ model parameter (including the bias term $	heta_0$ and the feature weights $	heta_1, 	heta_2, \dots, 	heta_n$).

This can be written more concisely using a vectorized form, as shown in Equation-4-2.

# Equation 4-2. Linear Regression model prediction (vectorized form)

```
$\hat{y} = h_	heta(x) = 	heta \cdot x$
```

+   - $	heta$ is the model's *parameter vector*, containing the bias term $	heta_0$ and the feature weights $	heta_1$ to $	heta_n$.
- $x$ is the instance's *feature vector*, containing $x_0$ with $x_0$ always equal to 1.
- $	heta \cdot x$ is the dot product of the vectors $	heta$ and $x$, which is of course equal to $	heta_0x_0 + 	heta_1x_1 + 	heta_2x_2 + \dots + 	heta_nx_n$.
- $h$ is the hypothesis function, using the model parameters $	heta$.

![](bbox=[0.178, 0.497, 0.238, 0.574])

In Machine Learning, others are often represented as column vectors, which are 2D arrays with a single column. If $	heta$ and $x$ are column vectors, then the prediction is $\hat{y} = 	heta^T x$, where $	heta^T$ is the transpose of $	heta$ (a row vector instead of a column vector) and $	heta^Tx$ is the matrix multiplication of $	heta^T$ and $x$. It is of course the same prediction, except it is represented as a single cell matrix rather than a scalar value. In this book we will use this notation to avoid switching between dot products and matrix multiplications.

Okay, that was the Linear Regression, so now how do we train it? Well, recall that training a model means setting its parameters so the model best fits the training data. For this purpose, we first need a measure of how well (or poorly) the model fits the training data. In Chapter 2 we saw that the most common performance measure of a regression model is the Root Mean Square Error (RMSE) (Equation 2-1). Therefore, to train a Linear Regression model, you need to find the value of $	heta$ that minimizes the RMSE. In practice, it is simpler to minimize the Mean Square Error (MSE)