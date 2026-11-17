# ## 2.6 This problem concerns the use of gradient descent in machine learning. Assume that the objective is to minimize the $L_2$ loss function for a simple linear regression problem as follows:

$$\hat{\beta}^{\text{LS}} = \arg\min_{\beta \in \mathbb{R}^2} \left[ \frac{1}{2} \sum_{i=1}^n (y_i - \mathbf{x}_i^T \beta)^2 \right].$$

What are the update equations for the least squares estimator? Note that it will take the form of:

$$\beta_j^{t+1} = \beta_j^t - \ell \times \frac{\partial f(\beta)}{\partial \beta_j}$$

where $j = 0$ or $1$, and $\ell$ is a predefined learning rate and $f(\beta)$ is the loss function.

# ## 2.7 (PROJECT) In this project, you will solve for the slope and intercept of a dataset using robust regression with Huber's method.

+   a) Import the needed libraries.

```
import numpy as np
from sklearn.linear_model import HuberRegressor
import matplotlib.pyplot as plt
```

+   b) Create data similar to the telephone data set.

```
np.random.seed(0)
X = np.linspace(0, 23, 24).reshape(-1, 1)
y = np.array([ 0.44, 0.47, 0.47, 0.59, 0.66, \n0.73, 0.81, 0.88, 1.06, 1.2 , \n1.35, 1.49, 1.61, 2.12, 11.9 , \n12.4 , 14.2 , 15.9 , 18.2 , 21.2 , \n4.3 , 2.4 , 2.7 , 2.9 ])
```

+   c) Fit the Huber regressor using the data.

```
huber = HuberRegressor(epsilon=4.0)
huber.fit(X, y)
slope = huber.coef_[0]
intercept = huber.intercept_
print("Slope=", f"{slope:.1f}", "Intercept=", f"{intercept:.1f}")
y_pred = huber.predict(X)
```

+   d) Plot the results.

```
plt.scatter(X, y, color='blue', label='Data points')
plt.plot(X, y_pred, color='red', \nlabel='Huber Regressor')
plt.xlabel('X')
plt.ylabel('y')
```