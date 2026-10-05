
## 1.4 Feature Engineering

We see that the least-squares optimization problem

$$\min_{w\in\mathbb{R}^d} ||\mathbf{X}w - \mathbf{y}||_2^2$$

represents the "best-fit" *linear* model, by projecting $y$ onto the subspace spanned by the columns of $\mathbf{X}$. However, the true input-output relationship $y=f(x)$ may be nonlinear, so it is useful to consider nonlinear models as well. It turns out we can still do this under the framework of linear least-squares, by augmenting the data with new **features**. In particular, we devise some function $\phi:\mathbb{R}^d\to\mathbb{R}^p$ that maps each data point $x\in\mathbb{R}^d$ to a vector of features $\phi(x)$. The component functions $\Phi\in\mathbb{R}^{n\times p}$, which has $\phi(x_i)$ as its $i$-th row, takes the place of:

$$\min_{w\in\mathbb{R}^p} ||\mathbf{\Phi}w - \mathbf{y}||_2^2$$

Note that the resulting model is still linear with respect to the features, but it is nonlinear with respect to the original data if $\phi$ is nonlinear. These are sometimes called **basis functions** because our hypothesis is a linear combination of them. In the simplest case, we could just use the components of $x$ as features (i.e. $\phi_j(x)=x_j$), but in the future it will sometimes be helpful to disambiguate the features of an example from the example itself, so we encourage this way of thinking.

### Example: Fitting Ellipses

Let's use least-squares to fit a model for data points that come from an ellipse.

- 1. **Applications and Data**: We have $n$ data points $\mathcal{D}=\{(x_{i,1},x_{i,2})\}_{i=1}^n$, which are noisy (could be the actual orbit). Our goal is to determine the relationship between the $x_1$ and $x_2$.

- 2. **Model**: Ellipse in the form $w_0+w_1x_1^2+w_2x_2^2+w_3x_1x_2+w_4x_1+w_5x_2=1$. There are 6 unknown coefficients (the weights).

- 3. **Optimization Problem**: We formulate the problem with least-squares:

$$\min ||\mathbf{\Phi}w - \mathbf{y}||_2^2$$

where

$$\Phi = \begin{pmatrix} x_{1,1}^2 & x_{1,2}^2 & x_{1,1}x_{1,2} & x_{1,1} & x_{1,2} \\ x_{2,1}^2 & x_{2,2}^2 & x_{2,1}x_{2,2} & x_{2,1} & x_{2,2} \\ \vdots & \vdots & \vdots & \vdots & \vdots \\ x_{n,1}^2 & x_{n,2}^2 & x_{n,1}x_{n,2} & x_{n,1} & x_{n,2} \end{pmatrix}$$

Note that there is no "target" vector $\mathbf{y}$, here this is not a traditional regression problem.

### Polynomial Features

One important class of features is **polynomial features**. Remember that a polynomial is a linear combination of monomial basis terms. Monomials can be classified in two ways, by their degree and dimension:

| degree $\to$ | 0 | 1 | 2 | 3 | ... |
| :--- | :--- | :--- | :--- | :--- | :--- |
| univariate | 1 | $x$ | $x^2$ | $x^3$ | ... |
| bivariate | 1 | $x_1, x_2$ | $x_1^2, x_2^2, x_1x_2$ | $x_1^3, x_2^3, x_1^2x_2$ | ... |

A reason we can use polynomial features is that any smooth function can be approximated arbitrarily. For this reason, polynomials are said to be universal approximators.

One downside of polynomials is that as their degree increase, their number of terms increases rapidly. Specifically, a polynomial of degree $d$ in $d$ dimensional space

$$\frac{(\ell+d)}{\ell} = \frac{(\ell+d)!}{\ell!}$$

terms. To get an idea for how quickly this grows, consider a few examples:

| $\frac{\ell}{d}$ | $\frac{(\ell+d)}{\ell}$ |

Later we will learn the kernel trick, a clever mathematical method that allows us to circumvent this rapidly growing cost in certain cases.

## 1.5 Hyperparameters and Validation

As before, consider a hypothesis of the form

$$h_w(\mathbf{x}) = \sum_{j=1}^p w_j \phi_j(\mathbf{x}) = \mathbf{w}^\intercal \phi(\mathbf{x})$$

Observe that the model order $p$ is not one of the decision variables optimized when we fit to the data. For this reason $p$ is called a hyperparameter. We might say more specifically that it is a model hyperparameter, ridge regression, which determines the structure of the model.

For another, recall ridge regression, when we add an $\ell^2$ penalty on the parameters $w$:

$$\min_{\mathbf{w}} ||\mathbf{X}\mathbf{w} - \mathbf{y}||_2^2 + \lambda ||\mathbf{w}||_2^2$$

The regularization parameter $\lambda$ controls the trade-off between fitting the training data and keeping the weights small. A larger $\lambda$ leads to a simpler model (more bias), while a smaller $\lambda$ allows for a more complex model (potential overfitting).

### Types of Error

Let us try to formally distinguish the types of error. Assume that the data are distributed according to some unknown distribution $\mathcal{D}$. The solution to the The problem is to set aside a portion (say 30%) of the data, to be called the validation set, which is disjoint from the training set.

| Validation | Training |
| :--- | :--- |

We can use this validation set to estimate the true error by the **validation error**:

$$\hat{R}_{VAL}(h) = \sum_{i=1}^m \ell(x_i^{val}), y_i^{val})$$

With this estimate, we have a simple method for choosing hyper values: a bunch of configurations of the hyperparameters and choose the one that yields the lowest validation error.

### The effect of hyperparameters on error

Note that as we add more features to a linear model, training error can only decrease. This is because the optimizer can set $w_i = 0$ if feature cannot be used to reduce training error.

![](img/99defe26aebed215976e83d281581f33_13_0.png

Adding more features tends to reduce true error as long as the additional features are useful predictors of the output. However, if we keep adding features, these begin to fit noise in the training data instead of the true signal, causing true error to actually increase. This phenomenon is known as **overfitting**.

![](img/99defe26aebed215976e83d281581f33_13_1.png

The validation error tracks the true error reasonably well as long as the validation set is reasonably large:

![](img/99defe26aebed215976e83d281581f33_13_2.png

The regularization hyperparameter $\lambda$ has a somewhat different effect on training error. Observe that if $\lambda = 0$, we recover the exact OLS problem, which is directly minimizing the training error. As $\lambda$ increases, the optimizer places less emphasis on the training error and more emphasis on reducing the magnitude of the parameters. This leads to a degradation in training error as $\lambda$ grows.
