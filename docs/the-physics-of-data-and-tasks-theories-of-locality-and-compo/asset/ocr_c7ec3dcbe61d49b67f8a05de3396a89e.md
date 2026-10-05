$\lambda_P = A\rho^{-a}$, $\kappa_0(P)/P \to 0$ as $P \to \infty$, both these operations result in an error that is asymptotically independent of $P$. Namely,

```
$$\frac{\kappa_0(P)}{P} = \frac{\kappa_0(1)}{P} \int_0^{\\infty} \frac{d\rho}{A\rho^{-a} + \kappa_0(\rho)/\rho} + \mathcal{O}(1) \quad (104)$
```

```
$$\frac{\kappa_0(P)}{P} = \frac{\kappa_0(1)}{P} \left( \frac{\kappa_0(\rho)}{\rho} \right) \int_0^{\\infty} \frac{d\sigma}{\sigma^{a-1} A_l^2 a}}{1 + \sigma} + \mathcal{O}(1)$
```

where on the side we changed the variable by $\sigma = \kappa_0(\rho)/(P)$. Since the integral in $\sigma$ is finite and independent of $P$, we find that $\kappa_0(P)/P = O(P^{-a})$. Similarly, we find that the mode-independent prefactor $\partial_l (\kappa_l(P)/P)|_{\lambda=0} = \mathcal{O}(1)$. As a result we work with left, modulo some $P$-independent prefactors

```
$$\mathcal{E}(P) \sim \sum_{\rho} \frac{\rho^{-2a}}{(A\rho^{-a} + P\rho^{-a})^2} |c_{\rho}|^2. \quad (105)$
```

Following the intuitive argument about the threshold role of $\kappa_0(P)/P \sim P^{-a}$, it is convenient to split the sum in Equation 105 into sectors where $\lambda_{\rho} \gg \kappa_0(P)/P$, $\lambda_{\rho} \sim \kappa_0(P)/P$, and $\lambda_{\rho} \ll \kappa_0(P)/P$, i.e.,

```
$$\mathcal{E}(P) \sim \sum_{\rho \ll P} \frac{\rho^{-2a}}{(A\rho^{-a})^2} |c_{\rho}|^2 + \sum_{\rho \sim P} |c_{\rho}|^2 + \sum_{\rho \gg P} |c_{\rho}|^2. \quad (106)$
```

Finally, Equation 28 is obtained by noting that, under our assumptions on the decay of $\mathcal{E}|c_{\rho}|^2$ with $\rho$, the contribution of the sum over $\rho \ll P$ is subleading in $P$ whereas the other two sums can be gathered together.

# A.2 NTKS OF CONVOLUTIONAL AND LOCALLY-CONNECTED NETWORKS

We begin this section by reviewing the computation of the NTK of a one-hidden-layer fully-connected network [COB19].

# Definition A.2.1 (one-hidden-layer FCN). A one-hidden-layer fully-connected network with H neurons is defined as follows,

```
$f^{FCN}(\mathbf{x}) = \frac{1}{\sqrt{H}} \sum_{h=1}^{H} a_h \sigma(\mathbf{w}_h^T\mathbf{x} + \mathbf{b}_h), \quad (107)$
```

where $\mathbf{x} \in \mathbb{R}^d$ is the input, $H$ is the width, $\sigma$ is a nonlinear activation function, $\{\mathbf{w}_h \in \mathbb{R}^d\}_{h=1}^H$ and $\{\mathbf{b}_h \in \mathbb{R}\}_{h=1}^H$ are the network's parameters.

Inserting Equation 107 into one obtains

```
$K^{FC}_{NTK,N}(\mathbf{x},\mathbf{y};\theta) = \frac{1}{H} \sum_{h=1}^{H} \sigma'(\\mathbf{w}_h^T\mathbf{x} + \mathbf{b}_h)\sigma'(\\mathbf{w}_h^T\mathbf{y} + \mathbf{b}_h) \\ + a_h^2\sigma'^2(\\mathbf{w}_h^T\mathbf{x} + \mathbf{b}_h)\sigma'(\\mathbf{w}_h^T\mathbf{y} + \mathbf{b}_h), \quad (108)$
```