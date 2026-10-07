So that we retain this characteristic of the cost function, we can write the cost function as follows:

```
$J = \sum_{i=1}^{m} y_i \log(\hat{p}_i) + (1 - y_i) \log(1 - \hat{p}_i)$
```

This can be expanded as:

```
$J = \sum_{i=1}^{m} [y_i \log(\sigma(y_i)) + (1 - y_i) \log(1 - \sigma(y_i))]$
= \sum_{i=1}^{m} [y_i \log(\frac{1}{1+e^{-y_i}}) + (1 - y_i) \log(1 - \frac{1}{1+e^{-y_i}})]$
```

You can expand it further by replacing $y_i = a_0 + a_1x_{i_1} + a_2x_{i_2} + \dots + a_nx_{n_i}$.

This cost function is called the Log-Loss Function. The Sigmoid Function is called the Logistic Function. Using the Sigmoid Function and the Log-Loss Function, this algorithm gets the name Logistic Regression algorithm.

We have reached a formula like the one used for the Linear Regression algorithm.

We need to minimize $J$ by altering the coefficients. We change the coefficients so that each iteration gives the coefficient as follows:

```
$a_i = a_i - \alpha \frac{\delta J}{\delta a_i}$ where $\alpha$ is the learning rate.
```

You may find it intimidating to find $\frac{\delta J}{\delta a_i}$. We have provided a simple method using the **sympy** library in Python, as shown in **Figure 4.9: