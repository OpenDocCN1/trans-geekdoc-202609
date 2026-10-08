If $c_m^{OLS} = 0$, then $c_m$ is minimal. Otherwise, the minimal $c_m$ has to have the same sign as $c_m^{OLS}$, since otherwise $c_m$ could be flipped and a smaller value could be achieved. Thus, it is equivalent to minimize

$$-Cc_m^{OLS} + \frac{1}{2}c_m^2 + \lambda \text{sgn}(c_m^{OLS})c_m.$$

Differentiating with respect to $c_m$ and setting to zero, gives

$$$c_m = c_m^{OLS} - \lambda \text{sgn}(c_m^{OLS})(|c_m^{OLS}|-\lambda)_{|c_m^{OLS}|>\lambda}.$$

To ensure $c_m$ has the same sign as $c_m^{OLS}$, we set $c_m = 0$, if $|c_m^{OLS}| < \lambda$. This effectively reduces the corresponding basis function by the modulus of $|c_m^{OLS}|$ by moving $\lambda$ towards zero. For $\lambda = 0$, we recover the OLS solution. If $\lambda$ is chosen too large, all coefficients are set to zero. Hence $\lambda$ needs to be chosen carefully, which can be done with a parameter search or cross-validation

$L_2$ regularization gives us

$$$\frac{1}{2}\|t\|^2 + \lambda\|c\|^2 = \frac{1}{2}t^T t - c^T D^T t + \frac{1}{2}c^T(D^T D + \lambda I)c.$$

The gradient of this function

$$-D(D^T D + \lambda I)c.$

Setting the gradient to zero, we have a minimum for

$$c = (D^T D + \lambda I)^{-1}D^T t,$$ \quad (S.3)$

since the matrix $D^T D + \lambda I$ is positive definite. If $D^T D$ is close to being singular, adding $\lambda$ to each diagonal term will move it away from singularity. This ridge regression stabilizes OLS.

It is interesting to consider the case of orthonormal basis functions $(D^T D = I)$. Then $L_2$ regularization reduces each component of the OLS solution by a factor of $(1+\lambda)^{-1}$. $L_1$ regularization on the other hand moves each component toward zero by $\lambda$. If the component is close to zero then $\lambda$ is set to zero. Elastic regularization combines the two effects.

Ridge regression is implemented in MATLAB as `ridge`, while LASSO is implemented as `lasso`. The latter also incorporates net regularization, since the elastic net becomes LASSO for $\lambda=1$. In Python `sklearn.linear_model` has representations of these and many other methods.

More, the $L_p$ norm is defined as

$$$||c||_p = \left( \sum_{m=1}^M |c_m|^p \right)^{1/p}.$$

Figure 8.9 shows the contour lines for various choices of $p$. The $L_2$ regularization does not favor any axes, while decreasing $p < 2$, the $L_p$ regularization