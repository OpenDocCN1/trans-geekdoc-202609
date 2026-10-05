
102 | Regression optimization

```
$\|w\|_p = \left(\sum_{i} |w_i|^p\right)^{\frac{1}{p}} \quad (5.17)$
```

such as the quadratic form of the $L^2$ norm

```
$\|w\|^2 = w_1^2 + w_2^2 + \dots \quad (5.18)$
```

or the Euclidean distance which is the $L^1$ norm,

```
$\|w\| = \sqrt{w_1^2 + w_2^2 + \dots} \quad (5.19)$
```

We can add this penalty term on the parameters to an unregularized loss function

```
$\hat{L}(\mathbf{w}; x, y) = L(\mathbf{w}; x, y) + \gamma\|w\| \quad (5.20)$
```

The loss $L(\mathbf{x}, y)$ is our regular loss function. For example, the previously used MSE objective can be modified

```
$\hat{L}(\mathbf{x}^{(i)}, y^{(i)}) = \frac{1}{2N} \sum_{i} (\mathbf{x}^{(i)} - y^{(i)})^2 + \gamma\|w\|^2 \quad (5.21)$
```

The hyperparameter $\gamma$ allows us to show how we should keep this constraint into account. The gradient descent of this regularized loss function with a quadratic penalty term is

```
$$\Delta\mathbf{w} = -\alpha \frac{dL(\mathbf{w}, x, y)}{d\mathbf{w}} - 2\gamma\mathbf{w} \quad (5.22)$$
```

which we can also write in the form

```
$$\mathbf{w} \leftarrow (1 - 2\alpha\gamma)\mathbf{w} - \alpha \frac{dL(\mathbf{w}, x, y)}{d\mathbf{w}} \quad (5.23)$$
```

This corresponds to an exponential decay of the weights when the gradient is 0. In other words, this puts pressure on the weights to decay unless they are reinforced by the gradient. This type of regularization is often called **weight decay**. This specific case of this quadratic penalty term is also called **ridge regression** or **Tikhonov regularization**.

Using the $L^1$ norm,

```
$\hat{L}(\mathbf{w}, x, y) = L(\mathbf{w}, x, y) - \gamma\|\mathbf{w}\| \quad (5.24)$
```

is related to a technique called LASSO (least absolute shrinkage and selection operator), in the case of linear regression with a quadratic loss function. This form of regularization leads to a constant weight decay.

```
$$\Delta\mathbf{w} = -2\alpha\gamma \text{sign}(\mathbf{w}) - \alpha \frac{dL(\mathbf{w}, x, y)}{d\mathbf{w}} \quad (5.25)$$
```

There is some argument that $L^2$ regularization leads to a more sparse representation than ridge regression. For example, it can be shown that this regularization works very well in situations where a few relevant features are embedded in a large and noisy vector with irrelevant features.

# Regularization: ridge regression and LASSO

It is useful to implement such methods directly from scratch, although we leave this as a useful exercise for the reader to undertake. In the following, we use the routines from sklearn to an instructive example. Here, we choose points from the linear model

```
$y = 0.5x_1 + 0.5x_2 \quad (5.26)$
```

and add some noise in the feature values. Our training points are $(x_1, x_2, y) = \{(0, 0, 0), (1, 0, 1), (2, 2, 2)\}$. The code for different versions of regularization is given here

- Listing 5 RidgeLasso.ipynb (with output)
```python
import numpy as np
from sklearn import linear_model
from mpl_toolkits.mplplot3d import Axes3D

```python
fig = plt.figure(); ax = fig.gca(projection='3d')

x = np.array([[0], [1], [2.1, 2]])
y = np.array([0, 1, 2])
ax.plot(x[:], x[:], y);
```

```python
reg = linear_model.Regression(); reg.fit(x, y)
print(reg.coef_)
ax.plot([0,2], [0,2], np.dot(reg.coef_, {2,2}));
```

```python
reg = linear_model.Ridge(alpha=.5); reg.fit(x, y)
print(reg.coef_)
ax.plot([0,2], [0,2], np.dot(reg.coef_, {2,2}));
```

```python
reg = linear_model.Lasso(alpha=0.1); reg.fit(x, y)
print(reg.coef_)
ax.plot([0,2], [0,2], np.dot(reg.coef_, {2,2}));
```

This program shows how to make 3-dimensional plots. The regression lines in this 3-dimensional plot are show in Fig. 5.4. The results look similar, but it is instructive to look at the coefficients, which are

> $w_1$

The values of linear regression without normalization are interesting as the value for the first parameter is compensated by the large negative value of the second parameter. While this works for the specific training points, generalization with other examples might not be so well. Ridge regression finds much similar to our original model. However, LASSO is also interesting as it finds a much smaller model can explain the data with only one parameter. This might be valuable in practical applications.

Regression is an important topic in machine learning, and there other methods are actively used. For example, we have already mentioned dropout which includes a certain probability that some of the parameters are set to 0 during the generation of an output during training. This is particularly useful in deep neural networks where it is thought to resembles biological processes as neurons sometimes do not fire

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_108_0.png)

Fig. 5.7 (linear regression without regularization and regularization with Ridge regression and Lasso.)

even with the same stimulus that would activate them at other times. In this way, it is necessary that the model is able to represent specific data points with a combination of other.

# Regression and optimization

## It is useful to implement such methods directly from scratch, although we leave this as a useful exercise for the reader to undertake. In the following, we use the routines from sklearn to an instructive example. Here, we choose points from the linear model

```
$y = 0.5x_1 + 0.5x_2 \quad (5.26)$
```

and add some noise in the feature values. Our training points are $(x_1, x_2, y) = \{(0, 0, 0), (1, 0, 1), (2, 2, 2)\}$. The code for different versions of regularization is given here

- Listing 5 RidgeLasso.ipynb (with output)
```python
import numpy as np
from sklearn import linear_model
from mpl_toolkits.mplplot3d import Axes3D

```python
fig = plt.figure(); ax = fig.gca(projection='3d')

x = np.array([[0], [1], [2.1, 2]])
y = np.array([0, 1, 2])
ax.plot(x[:], x[:], y);
```

```python
reg = linear_model.Regression(); reg.fit(x, y)
print(reg.coef_)
ax.plot([0,2], [0,2], np.dot(reg.coef_, {2,2}));
```

```python
reg = linear_model.Ridge(alpha=.5); reg.fit(x, y)
print(reg.coef_)
ax.plot([0,2], [0,2], np.dot(reg.coef_, {2,2}));
```

```python
reg = linear_model.Lasso(alpha=0.1); reg.fit(x, y)
print(reg.coef_)
ax.plot([0,2], [0,2], np.dot(reg.coef_, {2,2}));
```

This program shows how to make 3-dimensional plots. The regression lines in this 3-dimensional plot are show in Fig. 5.4. The results look similar, but it is instructive to look at the coefficients, which are

> $w_1$

The values of linear regression without normalization are interesting as the value for the first parameter is compensated by the large negative value of the second parameter. While this works for the specific training points, generalization with other examples might not be so well. Ridge regression finds much similar to our original model. However, LASSO is also interesting as it finds a much smaller model can explain the data with only one parameter. This might be valuable in practical applications.

Regression is an important topic in machine learning, and there other methods are actively used. For example, we have already mentioned dropout which includes a certain probability that some of the parameters are set to 0 during the generation of an output during training. This is particularly useful in deep neural networks where it is thought to resembles biological processes as neurons sometimes do not fire

## Non-linear regression

It is useful to implement such methods directly from scratch, although we leave this as a useful exercise for the reader to undertake. In the following, we use the routines from sklearn to an instructive example. Here, we choose points from the linear model

```
$y = 0.5x_1 + 0.5x_2 \quad (5.26)$
```

and add some noise in the feature values. Our training points are $(x_1, x_2, y) = \{(0, 0, 0), (1, 0, 1), (2, 2, 2)\}$. The code for different versions of regularization is given here

- Listing 5 RidgeLasso.ipynb (with output)
```python
import numpy as np
from sklearn import linear_model
from mpl_toolkits.mplplot3d import Axes3D

```python
fig = plt.figure(); ax = fig.gca(projection='3d')

x = np.array([[0], [1], [2.1, 2]])
y = np.array([0, 1, 2])
ax.plot(x[:], x[:], y);
```

```python
reg = linear_model.Regression(); reg.fit(x, y)
print(reg.coef_)
ax.plot([0,2], [0,2], np.dot(reg.coef_, {2,2}));
```

```python
reg = linear_model.Ridge(alpha=.5); reg.fit(x, y)
print(reg.coef_)
ax.plot([0,2], [0,2], np.dot(reg.coef_, {2,2}));
```

```python
reg = linear_model.Lasso(alpha=0.1); reg.fit(x, y)
print(reg.coef_)
ax.plot([0,2], [0,2], np.dot(reg.coef_, {2,2}));
```

This program shows how to make 3-dimensional plots. The regression lines in this 3-dimensional plot are show in Fig. 5.4. The results look similar, but it is instructive to look at the coefficients, which are

> $w_1$

The values of linear regression without normalization are interesting as the value for the first parameter is compensated by the large negative value of the second parameter. While this works for the specific training points, generalization with other examples might not be so well. Ridge regression finds much similar to our original model. However, LASSO is also interesting as it finds a much smaller model can explain the data with only one parameter. This might be valuable in practical applications.

Regression is an important topic in machine learning, and there other methods are actively used. For example, we have already mentioned dropout which includes a certain probability that some of the parameters are set to 0 during the generation of an output during training. This is particularly useful in deep neural networks where it is thought to resembles biological processes as neurons sometimes do not fire

## 5.5 Non-linear regression

Linear regression is often applied because relations in practical application can be at linear. It is also simple and offers a good starting point for experimenting with algorithms. Linear models are still important and should be considered a good first step. However, going beyond linear models is one of the gifts of modern machine learning. Allowing non-linear relations in a model opens the modeling to.

As a start point for discussing such cases, let us first consider a polynomial of order

```
$y = w_0 + w_1x^1 + w_2x^2 + \dots + w_nx^n = \sum_{i=0}^{n} w_ix^i \quad (5.30)$
```

We can fit this function to our house data with a gradient descent rule, noting that the derivative (we have only 1-dimension at the moment) is

```
$$\frac{dy}{dw_i} = x^i \quad (5.31)$$
```

Hence, the learning rule is

```
$w_i \leftarrow w_i - \alpha x^i \quad (5.32)$
```

A fit of the house data with a polynomial of order 12 is shown in Fig. 5.5A, and the corresponding loss values at the end of training in Fig. 5.5B. The loss becomes a little better over time, and it might be possible to reduce this further with more training iterations. The resulting regression curve captures some of the curvature of the data, although it seems unreasonable to assume that larger houses become cheaper after they reach a certain size.

While this polynomial function is fundamentally non-linear, it is interesting to note that we can cast the regression problem again into a linear framework. That can create a new feature vector $x$ with components $x_i = x^i$. We can then rewrite the model as

```
$y = \mathbf{w}^T\mathbf{x} \quad (5.33)$
```
