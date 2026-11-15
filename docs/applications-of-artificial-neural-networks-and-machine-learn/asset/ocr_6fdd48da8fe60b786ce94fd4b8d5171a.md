# ## 22.3.1 MARS

Multivariate adaptive regression splines is a nonlinear and nonparametric intelligent computing regression algorithm that models the nonlinear responses between the inputs and outputs of a system using a series of piecewise linear or cubic segments (splines). The resulting piecewise equation is known as the basis functions (BFs). The slope of regression function is allowed to change from one segment to the next. The end points of each segment are called knots. A knot marks the end of one region of data and the beginning of another. Unlike the well-known parametric linear regression analysis, MARS provides greater flexibility to explore nonlinear relation between a response variable and predictor variables. In addition, MARS also searches for possible interactions between variables by checking all degrees of interactions. Because it allows for all functional forms and interactions, MARS is able to track the complex data structures from high-dimensional datasets. The general MARS function can be expressed using the following equation:

```
\(\tilde{f}(x) = \beta_0 + \sum_{m=1}^M \beta_m \lambda_m(x)\) (22.9)
```

where \(\tilde{f}(x)\) is the predicted response, \(\beta_0\) and \(\beta_m\) are constants, which are estimated to yield the best data fit and _M_ is the number of basis functions included into the model. The basis function in MARS model can be either one single spline function, or a product of two or more spline functions for different predictor variables. The spline basis function, \(\lambda_m(x)\), can be specified as:

```
\(\lambda_m(x) = \prod_{k=1}^{k_m} [s_{km}(x_{v(k,m)} - t_{k,m})]\) (22.10)
```

where _k<sub>m</sub>_ is the number of knots, _s<sub>km</sub>_ takes either 1 or -1 and indicates the right/left regions of the associated step function, _v_(_k_, _m_) is the label of the predictor variable and _t<sub>k,m</sub>_ is the knot location.

MARS generates basis functions by searching in a stepwise manner. An adaptive regression algorithm is used for selecting the knot locations. An optimal MARS is developed through a two-stage forward and backward procedure. In the forward stage, MARS overfits data by considering a great number of basis functions. In the backward, to avoid overfitting, redundant basis functions are deleted from Eq. (22.9). MARS adopts Generalized Cross-Validation (GCV) to delete the redundant basis functions. The expression of GCV is given as:

```
\(GCV = \frac{\frac{1}{N} \sum_{i=1}^N [y_i - \hat{f}(x_i)]^2}{[1 - \frac{C(B)}{N}]^2}\) (22.11)
```