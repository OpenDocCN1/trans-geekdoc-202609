practice, the expected loss can be estimated empirically by averaging the loss over all of the training observations. The objective then becomes minimizing the quantity $R_{emp}$ defined as:

```
$R_{emp}(\theta) = \sum_{i=1}^{n} L(y_i, f(\mathbf{x}_i, \theta))$$
```

This process is called *empirical risk minimization*. The fact that this operation yields the appropriate estimator is an important result in machine learning. Details can be found in [38].

There is flexibility in selecting a loss function, but some attributes are important:

+   - Errors not to be measured as distances, as summing them would allow for cancellation

+   - It is preferable for the function to be continuously differentiable. This is because we will compute its gradient on the way to minimizing expected loss with respect to the function parameters. At points where a function is not differentiable, the gradient will not be defined.

Beyond this, the choice of loss function can depend on whether the SL task is regression or classification. The *squared error*, or L2 loss, is a popular choice for the regression task. Since the expected loss needs to be measured, the squared error can be averaged over the training set to produce the *mean squared error* (MSE) as follows:

```
$MSE = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$
```

Given the errors $y_i - \hat{y}_i$, are squared, their contributions are relatively small between -1 and 1, but they grow quadratically for larger values. This means that outliers will have a large influence on MSE (it is not a robust metric). Mathematically, MSE is continuously differentiable, making it straightforward to minimize with respect to parameters.

Next, let's look at a small example of calculating MSE with code.

```
import numpy as np

y_actual = np.array([1.1, 0.5, -1.2])
y_hat = np.array([1.2, 0.3, -1.3])

def mse(y, hat, logging=True):
    # compute errors
```