# 18.2.2 Nonstationary kernels

A stationary kernel assumes the measure of similarity between two inputs is independent of their location, i.e., $\mathcal{K}(\boldsymbol{x}, \boldsymbol{x}')$ only depends on $\boldsymbol{r} = \boldsymbol{x} - \boldsymbol{x}'$. A **nonstationary kernel** relaxes this assumption. This is useful for a variety of problems, such as environmental modeling (see e.g., [GSR12; Pat+22]), where correlations between locations can change depending on latent factors in the environment.

# 18.2.2.1 Polynomial kernels

A simple form of non-stationary kernel is the **polynomial kernel** (also called **dot product kernel**) of order $M$, defined by

$\mathcal{K}(\boldsymbol{x}, \boldsymbol{x}') = (\boldsymbol{x}^\top \boldsymbol{x}')^M$ (18.23)

This contains all monomials of order $M$. For example, if $M=2$, we get the **quadratic kernel**; in 2d, this becomes

$(\boldsymbol{x}^\top \boldsymbol{x}')^2 = (x_1 x'_1 + x_2 x'_2)^2 = (x_1 x'_1)^2 + (x_2 x_2)^2 + 2(x_1 x'_1)(x_2 x'_2)$ (18.24)

We can generalize this to contain all terms up to degree $M$ by using the **inhomogeneous polynomial kernel**

$\mathcal{K}(\boldsymbol{x}, \boldsymbol{x}') = (\boldsymbol{x}^\top \boldsymbol{x}' + c)^M$ (18.25)

For example, if $M=2$ and the inputs are 2d, we have

$(\boldsymbol{x}^\top \boldsymbol{x}' + 1)^2 = (x_1 x'_1)^2 + (x_1 x'_1)(x_2 x'_2) + (x_1 x'_1) + (x_2 x_2)(x_1 x'_1) + (x_2 x'_2)^2 + (x_2 x'_2) + (x_1 x'_1) + (x_2 x'_2) + 1$ (18.26)

# 18.2.2.2 Gibbs kernel

Consider an RBF kernel where the length scale hyper-parameter, and the signal variance hyper-parameter, are both input dependent; this is called the **Gibbs kernel** [Gib97], and is defined by

$\mathcal{K}(\boldsymbol{x}, \boldsymbol{x}') = \sigma(\boldsymbol{x})\sigma(\boldsymbol{x}')\sqrt{\frac{2\ell(\boldsymbol{x})\ell(\boldsymbol{x}')}{\ell(\boldsymbol{x})^2 + \ell(\boldsymbol{x}')^2}} \exp \left( - \frac{||\boldsymbol{x} - \boldsymbol{x}'||^2}{\ell(\boldsymbol{x})^2 + \ell(\boldsymbol{x}')^2} \right)$ (18.27)

If $\ell(\boldsymbol{x})$ and $\sigma(\boldsymbol{x})$ are constants, this reduces to the standard RBF kernel. We can model the functional dependency of these kernel parameters on the input by using another GP (see e.g., [Hei+16]).

# 18.2.2.3 Other non-stationary kernels

Other ways to induce non-stationarity include using a neural network kernel (Section 18.7.1), non-stationary spectral kernels [RHK17], or a deep GP (Section 18.7.3).