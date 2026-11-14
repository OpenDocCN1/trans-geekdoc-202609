We can marginalize out $z_n$ to get $p(y_n|x_n, \theta)$. If $y_n$ is a scalar, this becomes

$p(y_n|x_n, \theta) = \mathcal{N}(y_n|x_n^T v, w_y^T C w_y + \sigma_y^2)$ (28.100)
$C = (I + \sigma_x^{-2} W_x^T W_x)^{-1}$ (28.101)
$v = \sigma_x^{-2} C W_x w_y$ (28.102)

To apply this to the classification setting, we can replace the Gaussian $p(y|z)$ with a logistic regression model:

$p(y_n|z_n, \theta) = \text{Ber}(y_n|\sigma(w_y^T z_n))$ (28.103)

In this case, we can no longer compute the marginal posterior predictive $p(y_n|x_n, \theta)$ in closed form, but we can use techniques similar to exponential family PCA (see [Guo09] for details).

The above model is completely symmetric in $x$ and $y$. If our goal is to predict $y$ from $x$ via the latent bottleneck $z$, then we might want to upweight the likelihood term for $y$, as proposed in [Ris+08]. This gives

$p(X, Y, Z|\theta) = p(Y|Z, W_y)p(X|Z, W_x)^\alpha p(Z)$ (28.104)

where $\alpha \le 1$ controls the relative importance of modeling the two sources. The value of $\alpha$ can be chosen by cross-validation.

# 28.3.4.2 Partial least squares

We now consider an asymmetric or more “discriminative” form of supervised PCA. The key idea is to allow some of the (co)variance in the input features to be explained by its own subspace, $z_i^x$, and to let the rest of the subspace, $z_i^s$, be shared between input and output. The model has the form

$p(z_i) = \mathcal{N}(z_i^s|0, I_{L_s}) \mathcal{N}(z_i^x|0, I_{L_x})$ (28.105)
$p(y_i|z_i) = \mathcal{N}(W_y z_i^s + \mu_y, \sigma^2 I_{D_y})$ (28.106)
$p(x_i|z_i) = \mathcal{N}(W_x z_i^s + B_x z_i^x + \mu_x, \sigma^2 I_{D_x})$ (28.107)

See Figure 28.15b. The corresponding induced distribution on the visible variables has the form

$p(v_i|\theta) = \int \mathcal{N}(v_i|W z_i + \mu, \sigma^2 I) \mathcal{N}(z_i|0, I) dz_i = \mathcal{N}(v_i|\mu, W W^T + \sigma^2 I)$ (28.108)

where $v_i = (y_i; x_i)$, $\mu = (\mu_y; \mu_x)$ and

$W = \begin{pmatrix} W_y & 0 \\ W_x & B_x \end{pmatrix}$ (28.109)

$W W^T = \begin{pmatrix} W_y W_y^T & W_y W_x^T \\ W_x W_y^T & W_x W_x^T + B_x B_x^T \end{pmatrix}$ (28.110)

We should choose $L$ large enough so that the shared subspace does not capture covariate-specific variation.

MLE in this model is equivalent to the technique of partial least squares (PLS) [Gus01; Nou+02; Sun+09]. This model can be also be generalized to discrete data using the exponential family [Vir10].